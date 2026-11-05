# Day 03：Linux 用户与用户组管理

**日期：** 2026-11-05  
**系统：** Kali Linux

## 一、今日学习目标

学习 Linux 用户和用户组的实际管理，掌握以下命令：

| 命令 | 中文含义 |
|---|---|
| `groupadd` | 创建用户组 |
| `useradd` | 创建用户 |
| `usermod` | 修改用户账户 |
| `userdel` | 删除用户 |
| `groupdel` | 删除用户组 |
| `getent` | 查询系统数据库记录 |
| `id` | 查看用户身份和组关系 |

## 二、实验前检查

先检查测试用户和用户组是否已经存在：

```bash
getent passwd labuser    # 查询 labuser 用户是否存在
getent group labgroup    # 查询 labgroup 用户组是否存在
getent group labextra    # 查询 labextra 用户组是否存在
```

没有查询到记录时，`getent` 对指定记录返回退出状态码 `2`。

使用：

```bash
echo $?    # 查看上一条命令的退出状态码
```

注意：`$?` 只保存上一条命令的退出状态。

## 三、创建用户组 groupadd

```bash
sudo groupadd labgroup    # 使用管理员权限创建 labgroup 用户组
sudo groupadd labextra    # 使用管理员权限创建 labextra 用户组
```

参数解释：

- `sudo`：使用管理员权限执行命令。
- `groupadd`：创建用户组。
- `labgroup`、`labextra`：新用户组的名称。

验证：

```bash
getent group labgroup    # 查询 labgroup 用户组
getent group labextra    # 查询 labextra 用户组
```

实际结果：

- `labgroup` 的 GID 为 1001。
- `labextra` 的 GID 为 1002。

## 四、创建用户 useradd

```bash
sudo useradd -m -s /bin/bash -g labgroup labuser    # 创建 labuser，设置家目录、Shell 和主组
```

参数解释：

| 参数 | 含义 |
|---|---|
| `-m` | 创建用户家目录 |
| `-s` | 指定登录 Shell |
| `/bin/bash` | Bash Shell 的程序路径 |
| `-g` | 指定主组 |
| `labgroup` | 用户的主组 |
| `labuser` | 用户名 |

验证：

```bash
id labuser                    # 查看 labuser 的 UID、GID 和所属组
getent passwd labuser         # 查询 labuser 的账户记录
ls -ld /home/labuser          # 查看家目录本身的信息
```

实际结果：

- 用户名：`labuser`
- UID：1001
- 主组：`labgroup`
- 主组 GID：1001
- 家目录：`/home/labuser`
- Shell：`/bin/bash`

## 五、修改用户组关系 usermod

```bash
sudo usermod -aG labextra labuser    # 将 labextra 追加为 labuser 的附加组
```

参数解释：

- `usermod`：修改已有用户。
- `-a`：追加，不替换原有附加组。
- `-G`：指定附加组。
- `labextra`：要加入的组。
- `labuser`：要修改的用户。

验证：

```bash
id labuser    # 再次查看 labuser 的身份和组关系
```

实际结果：

```text
uid=1001(labuser) gid=1001(labgroup) groups=1001(labgroup),1002(labextra)
```

这说明：

- `labgroup` 是主组。
- `labextra` 是附加组。
- 用户成功加入了第二个组。

**重要区别：**

- `-g`：指定主组。
- `-G`：指定附加组列表。
- `-aG`：追加附加组，保留原有附加组关系。

## 六、清理实验账户

```bash
sudo userdel labuser       # 删除 labuser 用户账户
sudo groupdel labextra     # 删除 labextra 用户组
sudo groupdel labgroup     # 删除 labgroup 用户组
```

注意：这里使用的是 `userdel`，没有加 `-r`。因此用户家目录通常不会随账户删除，可能仍然保留在 `/home/labuser`。

如果要检查：

```bash
ls -ld /home/labuser    # 检查原来的家目录是否仍然存在
```

不要因为用户账户已经删除，就认为家目录也一定被删除。

## 七、实验中遇到的问题

曾经执行：

```bash
id labgroup    # 错误地把用户组名称当成用户名查询
```

系统返回：

```text
id: ‘labgroup’: 无此用户
```

原因：`id` 用于查询用户身份，而 `labgroup` 是用户组，不是用户名。

正确写法：

```bash
id labuser                 # 查询用户身份和组关系
getent group labgroup      # 查询用户组记录
```

## 八、今日命令中英对照

| 英文 | 中文联想 |
|---|---|
| user | 用户 |
| group | 用户组 |
| add | 添加 |
| del | 删除 |
| mod | 修改 |
| passwd | 用户账户数据库（在 getent passwd 中） |
| sudo | 管理员权限执行 |
| id | 身份信息 |
| -a | 追加 |
| -m | 创建家目录 |

## 九、今日总结

今天实际完成了：

1. 检查用户和用户组是否存在。
2. 创建 `labgroup` 和 `labextra`。
3. 创建 `labuser`。
4. 设置用户主组。
5. 使用 `usermod -aG` 添加附加组。
6. 使用 `id` 验证组关系。
7. 删除测试用户和用户组。

### Day 04 预告：Linux 进程管理

下一阶段学习：

- `ps`：查看进程
- `top`：动态查看系统进程
- `kill`：向进程发送信号

**学习提醒：** 英语单词暂时记不住没有关系。保留中文注释，结合实际操作反复练习，逐步建立命令记忆。