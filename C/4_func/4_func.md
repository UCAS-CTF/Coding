# Part 4: C语言-函数

Author: [RickT](https://github.com/RickT34)

<!-- * TOC
{:toc} -->

<font color=HotPink size=5>！注意：点击小箭头可以展开</font>

## 1. 函数基础

<details>
<summary>函数定义与调用</summary>
<br>
<div markdown="1">

函数的基本结构如下：
```c
返回类型 函数名(参数列表) {
    函数体
    return 返回值; // 可选
}
```
- **返回类型**：函数返回值的数据类型（如`int`, `void`）
- **函数名**：函数的唯一标识符
- **参数列表**：函数接受的输入参数（可空）
- **函数体**：包含具体执行的代码块
- **返回值**：使用`return`语句返回结果（`void`函数可省略）

</div>
</details>

### 练习1：简单无参数函数（函数基本使用）

<details>
<summary>无参数函数主要用来实现一些经常用到的简单功能，恰当的使用可以提高代码的可读性和可维护性。</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>

// 在此实现read_int函数，从控制台读取一个整数

int main() {
    int a = read_int();
    int b = read_int();
    printf("%d + %d = %d", a, b, a+b);
    return 0;
}
```

输入输出示例：
```
输入：
1
2
输出：
1 + 2 = 3
```

</div>
</details>

### 练习2：求最大值函数（带返回值的函数）

<details>
<summary>编写函数max，接收两个整数参数，返回较大的数。</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>

// 在此实现max函数

int main() {
    int x = 10, y = 20;
    printf("较大值是：%d", max(x, y)); 
    return 0;
}
```

输出示例：
```
较大值是：20
```

</div>
</details>

## 2. 函数参数

<details>
<summary>参数传递机制</summary>
<br>
<div markdown="1">

C语言参数传递特点：函数接收参数的**副本**，修改不影响原始变量


</div>
</details>

### 练习3：交换变量值实验

<details>
<summary>求程序的输出结果。</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>
void swap(int a, int b){
    int t = a;
    a = b;
    b = t;
}

int main(){
    int a = 5, b = 10;
    printf("交换前: a=%d, b=%d\n", a, b);
    swap(a, b);
    printf("交换后: a=%d, b=%d", a, b);
    printf("%d\n", a);
    return 0;
}
```

提示：正确的`swap`函数实现见"指针"章节。


</div>
</details>


## 3. 递归函数

<details>
<summary>递归原理</summary>
<br>
<div markdown="1">

什么是递归函数？

> 递归函数的定义：见“递归函数”

递归函数特征：
1. 包含**基线条件**（递归终止条件）
2. 包含**递归步骤**（调用自身的更小规模问题）
3. 每次调用创建新的栈帧

</div>
</details>

### 练习4：递归阶乘

<details>
<summary>使用递归实现阶乘函数factorial。</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>

int factorial(int n) {
    return _____ // 使用三目运算符实现递归
}

int main() {
    int n = 5;
    printf("%d! = %d", n, factorial(n));
    return 0;
}
```
输出示例：
```
5! = 120
```

</div>
</details>

### 练习5：斐波那契数列

<details>
<summary>使用递归实现斐波那契数列函数fib。</summary>
<br>
<div markdown="1">

斐波那契数列定义：
- fib(0) = 0
- fib(1) = 1
- fib(n) = fib(n-1) + fib(n-2) (n≥2)

输入输出示例：
```c
#include <stdio.h>

// 定义斐波那契数列函数

int main() {
    int n = 6;
    printf("fib(%d) = %d", n, fib(n));
    return 0;
}
```
输出示例：
```
fib(6) = 8
```

</div>
</details>


### 挑战题

<details>
<summary>使用递归求数列的第n项。</summary>
<br>
<div markdown="1">

数列定义：
- a(0) = 0, a(1) = 1
- b(0) = 1, b(1) = 1
- a(n) = b(n-1) + b(n-2)
- b(n) = a(n-1) + 2*a(n-2)

输入输出示例：
```c
#include <stdio.h>

// 定义数列函数

int main() {
    int n = 9;
    printf("a(%d) = %d, b(%d) = %d", n, a(n), n, b(n));
    return 0;
}
```
输出示例：
```
a(9) = 94, b(9) = 113
```


</div>
</details>

## 4. main函数

> 注：结合数组和指针学习会理解得更加透彻。

<details>
<summary>main函数的特殊地位</summary>
<br>
<div markdown="1">

`main`函数是C程序的入口点，具有以下特点：
- 程序执行的起点和终点
- 可以接受命令行参数
- 返回值为`int`类型，表示程序退出状态

### main函数的两种标准形式：
```c
// 无参数版本
int main(void) {
    return 0;
}

// 带参数版本  
int main(int argc, char *argv[]) {
    return 0;
}
```

</div>
</details>

### 练习6：命令行参数处理

<details>
<summary>编写程序计算命令行参数的和</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
    // 实现：计算所有命令行参数（整数）的和
    // 提示：使用atoi函数将字符串转换为整数
    
    return 0;
}
```

使用示例：
```bash
# 编译
gcc -o sum main.c

# 运行
./sum 10 20 30 40
```
输出：
```
total：100
```

要求：
1. 处理参数数量不正确的情况（至少需要2个数字）
2. 输出清晰的结果信息

</div>
</details>

### 练习7：简单的命令行计算器

<details>
<summary>实现支持加减乘除的命令行计算器</summary>
<br>
<div markdown="1">

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
    // 实现格式：./calc 运算符 数字1 数字2
    // 支持的运算符：+ - * /
    
    return 0;
}
```

使用示例：
```bash
./calc + 15 25      # 输出：15 + 25 = 40
./calc * 8 7        # 输出：8 * 7 = 56
./calc / 100 4      # 输出：100 / 4 = 25
```

要求：
1. 检查参数数量（必须为4个）
2. 处理除零错误
3. 支持浮点数运算
4. 处理无效运算符的情况

</div>
</details>