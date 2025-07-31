# Part 1：初识C语言

Author: [sikesibian](https://github.com/sikesibian)

<!-- * TOC
{:toc} -->

<font color=HotPink size=5>！注意：点击小箭头可以展开</font>

什么是C语言？

C语言是一种计算机程序设计语言，由Dennis Ritchie于1972年编写，由Unix操作系统的作者 Ken Thompson 改进，由Bell Labs的贝尔实验室开发。它是一种**通用的、面向过程式的高级语言**。你可能觉得这里的概念又多又抽象，但是不要紧，让我们一起来慢慢体会什么是C语言吧！


## 0. 准备工作

安装**gcc编译器**，在linux下使用apt命令即可，在windows下使用mingw-w64即可。

详情请参考[UCAS本科CTFwiki](https://ucas-ctf.github.io/)中第零讲中的讲义，补充资料与Q&A板块。

## 1. 编译并运行一个C语言程序

### 高级语言与编译

<details>
<summary>C语言与高级语言</summary>
<br>
<div markdown="1">

**语言是计算机程序设计语言，它定义了计算机程序如何被构建、运行、解释等，通俗地说就是定义了计算机工作的逻辑**。一般来说，语言分为高级语言和低级语言。其中**如C、C++、Java、Python等是高级语言**，人们可以用他们有效地去理解、表达更复杂的程序；而**汇编语言等低级语言**只能有效表达简单的程序，这些内容在后续都会触及。

不过**计算机并不能够直接理解高级语言（源代码）**，对于C语言这样的计算机高级语言，我们需要**编译器**来将高级语言转化为计算机可以理解的语言（机器语言），从而计算机去理解运行。这一过程就称为**编译**。

> - **C、C++、Go**等语言属于**编译型语言**，它们在执行前通过**编译器**转换成**机器语言或中间代码**。
> - **Python、Ruby、JavaScript、PHP**等语言属于**解释型语言**，它们的源代码在运行时由**解释器**逐行或逐块转换成机器语言并**立即执行**。

接下来让我们编译一个C语言程序。

1. 新建一个文件，命名为`hello.c`（当然这里可以使用任何名字，只要后缀为`.c`即可）
2. 输入以下代码：
```c
#include <stdio.h>
int main() {
    printf("Hello World!\n");
    return 0;
}
```
3. 保存文件，然后使用**命令行**编译：
```bash
gcc hello.c -o hello
```
4. 运行程序：
```bash
./hello
```
可以看到结果为：
```bash
Hello World!
```
5. 恭喜你，你已经成功运行了第一个C语言程序！
6. 如果你希望在命令行中直接运行，可以使用以下命令：
```bash
gcc hello.c -o hello && ./hello
```

现在让我们来解释一下上述各个操作中各个命令或参数的意义：

1. `gcc`：这个命令是GNU Compiler Collection（GCC）的缩写，它提供了C语言的编译器。
2. `hello.c`：这是要编译的文件名，它表示我们要编译的源代码文件。
3. `-o hello`：这个参数表示将编译后的可执行文件保存为`hello`，如果不加这个参数，编译后的文件名默认为`a.out`。
4. `&&`：这个符号表示前一个命令执行成功后，才执行下一个命令。
5. `./hello`：这个命令表示执行编译后的文件。这里的`./`表示当前目录。

</div>
</details>

## 2. 输入与输出

<details>
<summary>输入与输出</summary>
<br>
<div markdown="1">

在C语言中，输入和输出我们可以通过函数`scanf()`和`printf()`来实现。

下述代码片段展示了如何使用`scanf()`和`printf()`函数进行输入和输出。

```c
#include <stdio.h>
int main(){
    int a;
    scanf("%d", &a);
    printf("%d\n", a);
    return 0;
}
```

在C语言中，输入和输出的格式与`printf()`和`scanf()`函数的格式字符串中的格式符（format specifier）有关。具体请查询相关资料。

</div>
</details>

> 本篇后续的练习中，需要大家提前知道的知识点包括C语言中的**变量、数据类型、运算符、关键字**等概念。

### 练习1：输出数字（`printf`的基本使用）

<details>
<summary>补充完整下述程序并输出数字</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>
int main(){
    int a = 123;
    long b = 4567890123;
    long long c = 4567890123456789012;
    float d = 3.1415926;
    double e = 3.14159265358979323846;
    long double f = 3.141592653589793238462643383279502884197169399375105820974944592307816406286;
    // TODO
    // 输出a、b、c、d、e、f
    return 0;
}
```

输出示例：
```
a = 123
b = 4567890123
c = 4567890123456789012
d = 3.141593
e = 3.141593
f = 3.141593
```
</div>
</details>

### 练习2：输出不同进制下的数字（`printf`格式化字符串）

<details>
<summary>补充完整下述程序并输出不同进制下的数字</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>
int main(){
    int a = 123;
    // TODO:
    // 分别输出a的十进制、八进制、十六进制
    return 0;
}
```

输出示例：
```
a = 123
a = 0173
a = 0x7b
```

注：思考为什么这里输出是这个形式？

</div>
</details>

### 练习3：输入数字并输出（`scanf`的基本使用）

<details>
<summary>补充完整下述程序并根据输入数字输出数字</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>
int main(){
    int a;
    // TODO:
    // 输入一个数字并存储到a中
    printf("%d\n", a);
    return 0;
}
```

输入数据范围：`0 <= a <= 10000`

输入输出示例：
```
输入：
123
输出：
123
```

提示：
1. 当输入的字符串以换行符（`\n`）结尾时，`scanf()`结束输入。
2. 当输入的字符串以空格（` `）结尾时，`scanf()`会继续读取下一个字符，直到遇到换行符（`\n`）为止。
3. 当输入的字符串以制表符（`\t`）结尾时，`scanf()`会继续读取下一个字符，直到遇到换行符（`\n`）为止。

</div>
</details>

### 练习4：字符吞吐机（`scanf`对`\n`、` `等输入缓冲区中特殊字符的处理）

<details>
<summary>补充完整下述程序并根据输入字符输出字符</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>
int main(){
    char a, b, c;
    printf("Please input 3 characters: ");
    // TODO:
    // 使用scanf()读取三个字符，分别存储到a、b、c中，观察输出结果
    printf("Your characters are %c, %c and %c\n", a, b, c);
    return 0;
}
```

</div>
</details>

## 3. 数据类型

### 练习5：类型的存储大小和值范围（类型的存储大小和值范围）

> 你需要首先知道的概念：**字节、数据类型、数据类型的存储大小与取值范围**。

<details>
<summary>按顺序输出（当前编译器下）常见类型的存储大小</summary>
<br>
<div markdown="1">

常见的数据类型：`char`, `unsigned char`, `signed char`, `int`, `unsigned int`, `short`, `unsigned short`, `long`, `unsigned long`

无输出示例。

提示：**使用`sizeof()`函数可以获取一个变量或类型所占的字节数**。

</div>
</details>

### 练习6：浮点数的表示

> 请提前学习什么是浮点数，以及可以了解IEEE754浮点数标准。可以参考的：https://blog.csdn.net/weixin_45863060/article/details/125054244

<details>
<summary>请根据要求补充完整下述代码</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>
int main(){
    // 一般形式浮点数
    float a = 3.1415926;
    // 指数形式浮点数
    float b = 3.14e6;
    float c = 3.14e-6;
    float d = 3.14e+6;
    float e = -3.14e-6;
    // TODO:
    // 以指数形式输出a
    // 以一般形式输出b，但是仅保留小数点后3位
    // 以一般形式输出c，右对齐并占用宽度为10，保留2位小数
    // 以一般形式输出d，左对齐并占用宽度为16，保留3位小数
    // 以指数形式输出e
    return 0;
}
```
输出示例：
```
a = 3.141593e+00
b = 3140000.000
c =       0.00
d = 3140000.000
e = -3.140000e-06
```

</div>
</details>

### 练习7：数字的运算（类型转换，运算符）

<details>
<summary>类型转换</summary>
<br>
<div markdown="1">

提醒：
```
                                         float
short                                      |
     \                                     v
      +--> int --> unsigned --> long --> double
     /
 char
```

- 将一种类型的数据赋值给另外一种类型的变量时就会发生自动类型转换。而在赋值运算中，赋值号两边的数据类型不同时，需要把右边表达式的类型转换为左边变量的类型，这可能会导致数据失真，或者精度降低。

- 在不同类型的混合运算中，编译器也会自动地转换数据类型，将参与运算的所有数据先转换为同一种类型，然后再进行计算。
    - `char` 和 `short` 参与运算时，必须先转换成 `int` 类型
    - 转换按数据长度增加的方向进行，以尽量保证数值不失真或精度不降低
    - 所有的浮点运算都是以双精度进行的

</div>
</details>

<details>
<summary>根据输入按序输出要求的结果</summary>
<br>
<div markdown="1">

```c
#include<stdio.h>

int main() {
    double a, b;
    scanf("%lf %lf", &a, &b);
    // TODO:
    // 输出a和b的加减乘除结果
    // 输出 a 除以 b整数部分 的结果
    // 输出 a整数部分 除以 b 的结果
    // 输出 a 和 b 的取整结果
    // 输出 a整数部分 和 b整数部分 的商和余数
    // 输出 a整数部分 除以 b整数部分 的结果的整数部分
    // 输出 a整数部分 除以 b整数部分 的结果
    return 0;
}
```

输入输出示例：
```
输入：
3.1415926 2.7182818
输出：
5.859874
0.423311
8.539734
1.155727
1.570796
1.103638
3
2
1 1
1
1.500000
```

</div>
</details>


