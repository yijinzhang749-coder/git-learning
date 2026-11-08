# Python 小课堂 01：变量与基本数据类型

## 一、学习目标

1. 认识 Python。
2. 理解变量的作用。
3. 学会使用 print() 输出内容。
4. 认识四种基本数据类型。
5. 学会使用 type() 检查数据类型。
6. 将变量和简单的登录系统联系起来。

## 二、什么是变量？

变量（Variable）可以理解为一个有名字的储物盒，用来保存数据。

例如：

```python
name = "Kali"
age = 20
```

其中：

- `name`：变量名。
- `"Kali"`：保存的字符串。
- `age`：变量名。
- `20`：保存的整数。
- `=`：赋值符号，将右边的数据赋给左边的变量。

注意：

Python 中的 `=` 表示赋值，不是数学中的相等判断。

## 三、使用 print() 输出内容

`print()` 的作用是把内容输出到控制台。

```python
print("Hello, Python!")
```

输出：

```text
Hello, Python!
```

### 直接输出和变量输出的区别

```python
username = "admin"

print(username)
print("username")
```

输出：

```text
admin
username
```

区别：

- `print(username)`：读取变量中的值。
- `print("username")`：直接输出字符串 `username`。

**重要：** 使用变量名时不要加引号；如果加了引号，Python 就会把它当成普通文本。

## 四、Python 四种基本数据类型

### 1. 字符串（String）

类型名称：`str`

用于保存文本。

```python
username = "admin"
```

字符串通常使用单引号或双引号包围。

### 2. 整数（Integer）

类型名称：`int`

用于保存整数。

```python
failed_count = 5
```

整数可以用于计数和数学计算。

### 3. 浮点数（Float）

类型名称：`float`

用于保存带小数部分的数字。

```python
height = 1.75
```

注意：float 并不保证所有小数都能精确表示。

例如：

```python
print(0.1 + 0.2)
```

结果可能是：

```text
0.30000000000000004
```

如果涉及精确的金额计算，可以了解 Python 的 `Decimal`。

### 4. 布尔值（Boolean）

类型名称：`bool`

只有两个基本值：

- `True`：真、成立。
- `False`：假、不成立。

例如：

```python
locked = True
```

注意：

`True` 和 `False` 首字母必须大写，而且不加引号。

如果写成：

```python
locked = "True"
```

得到的是字符串，而不是布尔值。

## 五、数字和字符串的区别

这是 Python 初学者需要重点掌握的知识。

```python
a = 5
b = "5"
```

两者看起来相似，但数据类型不同：

- `5` 是整数，可以参与数字计算。
- `"5"` 是字符串，是一段文本。

例如：

```python
print(5 + 1)
```

输出：

```text
6
```

但：

```python
print("5" + "1")
```

输出：

```text
51
```

因为两个字符串进行 `+` 操作时，会进行字符串拼接。

## 六、使用 type() 检查数据类型

`type()` 用于查看一个数据或变量的类型。

示例：

```python
username = "admin"
failed_count = 5
height = 1.75
locked = True

print(type(username))
print(type(failed_count))
print(type(height))
print(type(locked))
```

输出：

```text
<class 'str'>
<class 'int'>
<class 'float'>
<class 'bool'>
```

对应关系：

| 输出 | 数据类型 | 中文 |
|---|---|---|
| `str` | String | 字符串 |
| `int` | Integer | 整数 |
| `float` | Float | 浮点数 |
| `bool` | Boolean | 布尔值 |

## 七、今天独立完成的代码

```python
username = "admin"
failed_count = 6
locked = True

print(username)
print(failed_count)
print(locked)

print(type(username))
print(type(failed_count))
print(type(locked))
```

输出的变量值：

```text
admin
6
True
```

输出的数据类型：

```text
<class 'str'>
<class 'int'>
<class 'bool'>
```

## 八、安全思维：模拟登录系统

今天用变量模拟了一个简单的登录系统。

```python
username = "admin"
password_correct = False
failed_count = 3
locked = False
```

各变量的含义：

| 变量 | 含义 | 类型 |
|---|---|---|
| `username` | 用户名 | `str` |
| `password_correct` | 密码是否正确 | `bool` |
| `failed_count` | 登录失败次数 | `int` |
| `locked` | 账户是否锁定 | `bool` |

### 重要理解

1. 密码是否正确和账户是否锁定是不同的状态。
2. 失败次数达到规定阈值时，可以触发账户锁定。
3. 即使密码正确，账户已锁定时也不应直接允许登录。
4. 失败次数记录的是数量，账户锁定记录的是状态。

真实登录系统还需要考虑密码安全存储、登录限制、会话管理和权限验证等问题。今天只是进行基础的数据建模，并没有实现真正的认证系统。

## 九、技术英语词汇

| 英文 | 中文 |
|---|---|
| variable | 变量 |
| integer | 整数 |
| string | 字符串 |
| float | 浮点数 |
| boolean | 布尔值 |
| print | 打印、输出 |
| type | 类型 |

## 十、今天的学习记录

已经实际完成：

- 使用 PyCharm 创建 Python 文件。
- 运行第一个 Python 程序。
- 创建变量并赋值。
- 使用 `print()` 输出变量。
- 区分变量名和字符串。
- 区分数字和数字字符串。
- 认识 `str`、`int`、`float`、`bool`。
- 使用 `type()` 检查数据类型。
- 用变量模拟简单登录系统的数据状态。

目前阶段评价：

- 变量赋值：L3 初步达成
- 基本数据类型：L2–L3
- `print()` 和 `type()`：L3 基础操作
- 登录系统数据建模：L2

这些评价只针对今天实际练习过的内容。尚未验证独立编写完整程序、条件判断、循环和函数的能力。

## 十一、复习题

1. `5` 和 `"5"` 有什么区别？
2. `True` 和 `"True"` 有什么区别？
3. `print(username)` 和 `print("username")` 有什么区别？
4. `type()` 有什么作用？
5. 为什么登录失败次数适合用整数？
6. 为什么账户是否锁定适合用布尔值？
7. `float` 是否一定能精确表示所有小数？

---

**Python 小课堂 01 笔记结束。**