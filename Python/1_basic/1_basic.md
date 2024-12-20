# Part 1：初识Python

Author: [sikesibian](https://github.com/sikesibian)

* TOC
{:toc}

> 对于 Python 我们将忽略最基础的内容。最基本的语法请朋友们根据相关资料（如 菜鸟教程、莫烦Python）进行学习。当然在每个板块之前我们也会再强调朋友们需要学习的基本知识。

## 1. 变量与运算

### 练习1：`input`，`print`的基本使用

> 请学习了解 Python 中的 **变量**、**运算符**、**数据类型**、**`print` 函数** 以及 **`input` 函数**。

<details>
<summary>（点击展开）Hello, World!</summary>
<br>
<div markdown="1">

接收一个字符串 `name`，输出 `Hello, <name>!`

输入输出示例：
```
输入：
Please input your name: UCAS CTF
输出：
Hello, UCAS CTF!
```
</div>
</details>

### 练习2：`print` 的格式化输出

> 请学习 Python 中 `print` 函数的 **格式化输出**。

<details>
<summary>（点击展开）自我介绍</summary>
<br>
<div markdown="1">

请你设计一个程序接收用户的基本信息并生成一个固定格式的自我介绍。

输入输出示例：
```
输入：
Your name: UCAS CTF
Your age: 18
Your gender: male
Your major: Computer Science and Technology
Your hometown: Beijing
输出：
Hello! I'm UCAS CTF, an 18-year-old male from Beijing, currently majoring in Computer Science and Technology. Always ready to learn and innovate, I'm excited about what the future holds in the world of tech!
```

注：你可以使用多种方式实现上述程序。比如**格式化字符串（`format`扩展选项、`f"string{var}"`等等）**。

</div>
</details>

### 练习3：条件语句、运算符

> 请学习 Python 中的 **运算符**。

<details>
<summary>（点击展开）简易计算器</summary>
<br>
<div markdown="1">

> 请学习 Python 中的 **条件语句**（`if`、`elif`、`else`）、基本的**运算符**
> 
> - `+`：加法，`-`：减法，`*`：乘法，`/`：除法，`//`：取商，`%`：取余，`**`：指数。
> - `==`：判断两个数是否相等，`!=`：判断两个数是否不相等。
> - `>`：判断一个数是否大于另一个数，`>=`：判断一个数是否大于等于另一个数，`<`：判断一个数是否小于另一个数，`<=`：判断一个数是否小于等于另一个数。
> - `and`：逻辑与，`or`：逻辑或，`not`：逻辑非。
> - `is`：判断两个变量是否指向同一个对象，`is not`：判断两个变量是否指向不同的对象。（常见用法：`a is not None`）

补充完整下述代码：
```python
a = int(input("Please input number a: ").strip())
b = int(input("Please input number b: ").strip())
op = input("Please input operation: ").strip()

if op == "+":
    print("Performing Addition ...")
    print(f"{a} {op} {b} = {a + b}")
elif op == "-":
    print("Performing Subtraction ...")
    # TODO
elif op == "*":
    print("Performing Multiplication ...")
    # TODO
elif op == "/":
    print("Performing Division ...")
    print("I will give you the remainder and quotient.")
    # TODO
elif op == "**":
    print("Performing Exponentiation ...")
    # TODO
else:
    print("Invalid Operation!")
```

注：详细输出格式请看下述示例：

输入输出示例：

```
输入：
Please input number a: 5
Please input number b: 3
Please input operation: +
输出：
Performing Addition ...
5 + 3 = 8
```

```
输入：
Please input number a: 5
Please input number b: 0
Please input operation: /
输出：
Performing Division ...
Invalid Operation!
```

```
输入：
Please input number a: 5
Please input number b: 3
Please input operation: /
输出：
Performing Division ...
I will give you the remainder and quotient.
5 / 3 = 1 ... 2
```


</div>
</details>

### 练习4.1：列表与元组

> 请学习 Python 中的 **列表类型 list** 和 **元组类型 tuple** 。

<details>
<summary>（点击展开）尝试给出并理解下述代码的运行结果</summary>
<br>
<div markdown="1">

**对于列表类型，我们常用的运算符有**：

- `+`：列表的连接，`*`：列表的复制
- `in`：判断元素是否在列表中
- `[::]`：切片
- `sort`：排序，`sorted`：排序后生成新列表
- `len`：获取列表的长度
- `max`：获取列表中的最大值，`min`：获取列表中的最小值
- `sum`：求和
- `*`：解包
- `count`：统计元组中某个元素出现的次数
- `index`：获取元组中某个元素在元组中的位置
- `append`：在列表末尾添加元素
- `remove`：删除列表中某个元素
- `insert`：在列表中指定位置插入元素
- `reverse`：反转列表
- `extend`：在列表末尾扩展多个元素

```python
a = [1, 5, 6, 2, 3, 4, 7, 8, 9, 10]
print(sum(a))
print(len(a + a + a * 2))
print(a[-1])
print(a[:-1])
print(a[::-1])
print(sorted(a))
a = [1, 5, 6, 2, 3, 4, 7, 8, 9, 10]
print(a); print(a.sort()); print(a)
print(max(a) - min(a))
print(a.count(1))
print(a.index(1))
a.extend([11, 12, 13, 14, 15])
a.append(16)
a.append(a)
print(a)
a.remove(1)
print(a)
a.insert(0, 1)
print(a)
a.reverse()
print(a)
print(a[0])
print(a[0][0])
```

**思考**：
- 如何构造一个全部由 1 组成的长为 `n` 的列表？
- 如何将一个列表倒序？
- `sort` 和 `sorted` 的区别？

**对于元组类型，我们常用的运算符有**：
- `+`：元组的连接，`*`：元组的复制
- `in`：判断元素是否在元组中
- `*`：解包
- `len`：获取元组的长度
- `max`：获取元组中的最大值，`min`：获取元组中的最小值
- `sum`：求和
- `count`：统计元组中某个元素出现的次数
- `index`：获取元组中某个元素在元组中的位置

```python
a = (1, 5, 6, 2, 3, 4, 7, 8, 9, 10)
print(sum(a))
print(len(a + a + a * 2))
print(a[-1])
print(a[:-1])
print(a[::-1])
print(sorted(a), type(sorted(a)))
print(max(a) - min(a))
print(a.count(1))
print(a.index(1))
```

思考：
- 元组能否有 `a.sort()` ？


</div>
</details>

### 练习4.2：字典

> 请学习 Python 中的 **字典类型 dict**。

<details>
<summary>（点击展开）尝试给出并理解下述代码的运行结果</summary>
<br>
<div markdown="1">

</div>
</details>

### 练习4.3：集合

> 请学习 Python 中的 **集合类型 set**。

<details>
<summary>（点击展开）尝试给出并理解下述代码的运行结果</summary>
<br>
<div markdown="1">

</div>
</details>

### 练习4.4：打包、解包

> 请学习 Python 中的 **打包、解包**。
>
> - `*`，`**`
> - `zip`，`enumerate`，`map`，`filter`，`reduce`


<details>
<summary>（点击展开）尝试给出并理解下述代码的运行结果</summary>
<br>
<div markdown="1">

</div>
</details>

### 练习5：循环语句

> 请学习 Python 中 **`print` 的 `end` 选项和 `sep` 选项**
> 
> 请学习 Python 中的 **条件语句**（`if`、`elif`、`else`）、**循环语句**（`for i in range(n)`、`while`） 。

<details>
<summary>（点击展开）完全 k 方数</summary>
<br>
<div markdown="1">

利用下述代码可以每行十个地输出 1 到 n 的完全平方数（完全 2 方数）。

```python
n = int(input("Please input a number: "))
if n <= 0: print("Invalid input!")
i = 1
while i ** 2 <= n:
    print(i ** 2, end=" ")
    i += 1
    if i % 10 == 1: print()
```

请设计一个 Python 程序，接收一个正整数 n 和 正整数 k，输出 n 的完全 k 方数。

**额外的思考：阅读下面的几种完全平方数的实现并对实现方法和效率问题进行思考**。

注：**海象运算符**：

```python
n = int(input("Please input a number: "))
if n <= 0: print("Invalid input!")
i = 0
while (i + 1) ** 2 <= n:
    print((i := i + 1) ** 2, end=" ")
    if i % 10 == 0: print()
```

注：**列表推导式**：

```python
n = int(input("Please input a number: "))
if n <= 0: print("Invalid input!")
print("\n".join(" ".join(f"{j ** 2}" for j in range(i, i + 10) if j ** 2 <= n) for i in range(1, n + 1, 10) if i ** 2 <= n))
```

或许下面这种写法会更好看一些：
```python
n = int(input("Please input a number: "))
if n <= 0: print("Invalid input!")
print(
    "\n".join(
        " ".join(
            f"{j ** 2}" for j in range(i, i + 10) if j ** 2 <= n
            ) 
        for i in range(1, n + 1, 10) if i ** 2 <= n
        )
    )
```

</div>
</details>


### 练习6：类型转换（数字、进制数字、字符、字节类型）

> 请学习 **`int`函数**，**`hex`函数** 和 **`bin`函数**，**`ord`函数** 和 **`chr`函数**。
> 
> 请学习字符串的 **`join` 方法与`zfill`方法**。
> 
> 请学习 **`bytes` 函数** 将整数列表转换为 `bytes` 类型。

<details>
<summary>补充完整下述程序并根据输入数字输出数字</summary>
<br>
<div markdown="1">

输入上接收一串二进制数据（不以 `0b` 开头），将它转换为十六进制数据，和可见字符串，并以一定格式输出：
- 末尾自动补0
- 输出上分两栏，左栏是十六进制数据，右栏是可见字符串（ascii 32~126），左右栏之间相隔 6 个空格。
- 输出的左栏的十六进制数据以 1 个字节为单位用空格隔开，每行最多 10 个字节。
- 输出的右栏的字符串与左栏的十六进制数据一一对应，如果字符无法显示则用 `.` 代替（包括换行符、制表符等）。
- 最后将数据转换为 `bytes` 类型进行输出。

输入输出示例：  

```
输入：
0100011000111010110100111011001101000001100000111110010010110000010100101111011101010001010000111100001001110101001001010101010100011110101001111000110001001000110010001010101011111010111001010110001110001101100111001011010000100011010001111011110001011100011011110101010011000100100110100011010110011001010100111110110000001101101111011100101111011111100111010100011001110110101010000110011010000000001101100000010011010010100010111111
输出：
46 3a d3 b3 41 83 e4 b0 52 f7      F:..A...R.
1e a7 8c 48 c8 aa fa e5 63 8d      ...H....c.
6f 54 c4 9a 35 99 53 ec 0d bd      oT..5.S...
66 80 36 04 d2 8b f0               f.6....
b'F:\xd3\xb3A\x83\xe4\xb0R\xf7QC\xc2u%U\x1e\xa7\x8cH\xc8\xaa\xfa\xe5c\x8d\x9c\xb4#G\xbc\\oT\xc4\x9a5\x99S\xec\r\xbd\xcb\xdf\x9dFv\xa8f\x806\x04\xd2\x8b\xf0'
```

</div>
</details>

## 2. 函数与模块

### 练习7：函数的定义

> 请学习 Python 中的 **函数定义**。

<details>
<summary>（点击展开）</summary>
<br>
<div markdown="1">

</div>
</details>