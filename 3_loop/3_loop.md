# Part 3: C语言-循环语句

Author: [Sikesibian](https://github.com/sikesibian)

* TOC
{:toc}

<font color=HotPink size=5>！注意：点击小箭头可以展开</font>

## 1. for循环语句

<details>
<summary>for循环描述</summary>
<br>
<div markdown="1">

for循环语句的格式如下：
```c
for(初始化语句 ; 循环条件 ; 循环步长){
    循环体
}
```
- **初始化语句**：在**循环开始前**执行，只执行一次
- **循环条件**：在**循环体开始前**执行
- **循环步长**：在**循环体结束后**执行
- **循环体**：循环主体代码。

</div>
</details>

### 练习1：阶乘（for循环的基本使用）

<details>
<summary>输入一个整数n，输出n!的结果。</summary>
<br>
<div markdown="1">

输入数据范围：`-100 <= n <= 100`

输入输出示例：
```
输入：
5
输出：
120
```
```
输入：
-6
输出：
Invalid Input
```

</div>
</details>

### 练习2：简单的素数判定（for循环嵌套条件语句）

<details>
<summary>输入一个正整数n，判断n是否为素数。</summary>
<br>
<div markdown="1">

输入数据范围：`1 <= n <= 100000`

输入输出示例：
```
输入：
13
输出：
Yes
```
```
输入：
15
输出：
No
```

**提示：**
1. 素数是正整数，并且除了1和自身以外，没有其他因数。
2. 1不是素数。
3. 2是素数。

</div>
</details>

### 练习3：输出一个数的所有因数（for循环嵌套条件语句）

<details>
<summary>输入一个正整数n，输出n的所有真因数。</summary>
<br>
<div markdown="1">

输入数据范围：`1 <= n <= 100000`

输入输出示例：
```
输入：
12
输出：
1, 2, 3, 4, 6, 12
```

**提示：**
1. 真因数不包括自身。

</div>
</details>

### 练习4：输出一个数的所有素因数（for循环嵌套for循环语句）

<details>
<summary>输入一个正整数n，输出n的所有素因数。</summary>
<br>
<div markdown="1">

输入数据范围：`1 <= n <= 100000`

输入输出示例：
```
输入：
12
输出：
2, 3
```

</div>
</details>



### 练习5：控制流平坦化（for循环嵌套switch语句）

<details>
<summary>控制流</summary>
<br>
<div markdown="1">

**控制流**往往指的是**计算机执行一个程序中语句的顺序**。程序会从第一行代码开始执行直至最后一行，除非**遇到（实际中是非常普遍地）改变控制流**的代码结构，比**如条件语句和循环**。控制流往往有三种结构：**顺序结构、循环结构和分支结构（可以理解为跳转）**。

> - **基本块**：函数控制流图中的最小基本块，**只有一个“入口”和一个“出口”，且只能从其“入口”进入，从“出口”退出**。**中间没有跳转**（如条件跳转，循环跳转，函数跳转或返回等）。值得一提的是：**只要基本块中第一条指令被执行了，那么基本块内所有执行都会按照顺序仅执行一次**。
> - **控制流图（Control Flow Graph, CFG）** ：是过程或程序的抽象表示，**代表了一个程序执行过程中会走过的所有路径**，它使用一个图的形式来**表示所有基本块可能从哪儿来，到哪儿去**。是之后会学习到的编译优化与静态分析的重要工具之一。

对于下述代码片段：   

```c
int A, B, C;
scanf("%d %d %d", &A, &B, &C);
if (A == 10) {
    if (B > C) {
        A = B;
    }
    else {
        A = C;
    }
}
printf("%d %d %d\n", A, B, C);
```

那么它的控制流图可以近似理解为：   

![](/bin/3_loop/img/3_5_1.svg)

</div>
</details>

<details>
<summary>练习：理解循环语句的控制流</summary>
<br>
<div markdown="1">

仿照上述示例，绘制下述代码中指定片段的控制流图：  

```c
# include <stdio.h>
int main() {
    int i, j, line = 0;
    int n;
    scanf("%d", &n);
    // the beginning of the code snippet
    for (i = 0, j = 1; j <= n; i ++, j ++) {
        printf("*");
        if (i == line) {printf("\n"); i = -1; line ++;}
    }
    if (i != 0) {printf("\n");}
    // the end of the code snippet
    return 0;
}
```

</div>
</details>


<details>
<summary>控制流平坦化</summary>
<br>
<div markdown="1">

**控制流平坦化（control flow flattening）** 实际上是一种作用于**控制流图**的**代码混淆**技术，其基本思想是**重新组织函数控制流图中基本块的关系**。细节内容可参考文献：[*Obfuscating C++ Programs via Control Flow Flattening*](<obfuscating c++ programs via control flow flattening.pdf>)  

> **代码混淆（Obfuscated Code）**：代码混淆是一种保护程序代码，如源代码（版权，漏洞分析难度等），的安全技术，**其将计算机程序的代码转换为一种功能上等价，但是阅读和理解更难的形式**。  

**控制流平坦化通过插入一个“主发生器”来负责控制程序的执行流，它将基本块间的前后关系进行混淆**，从而加大敌手拿到代码后的阅读分析的难度。   

比如上述给出的控制流图：  

![](/bin/3_loop/img/3_5_1.svg)

对它们进行编号：

![](/bin/3_loop/img/3_5_2.svg)

其平坦化后即可以写为为：  

![](/bin/3_loop/img/3_5_3.svg)

具体的代码可以写为：  
```c
# include <stdio.h>

int main(){
    int state = 1;
    for (;state != -1;){
        switch (state){
            case 1:
                int A, B, C;
                scanf("%d %d %d", &A, &B, &C);
                if (A == 10) state = 2;       
                else state = 6;
                break;
            case 2:
                if (B > C) state = 3;
                else state = 4;
                break;
            case 3:
                A = B;
                state = 5;
                break;
            case 4:
                A = C;
                state = 5;
                break;
            case 5:
                state = 6;
                break;
            case 6:
                printf("%d %d %d\n", A, B, C);
                state = -1;
                break;
            }
        }
    return 0;
}
```

**思考下面的问题**：
1. **`state`变量**在代码中起到了什么作用？
2. 每一个 **`case i`块中的内容**，抽象地说，一般我们认为由**两部分**组成，分别是哪两部分？
3. 每一个 **`case i`块中的内容**与最开始我们给出的**控制流图、刚刚对基本块编过号的控制流图**有什么关系？
4. 你能简单**总结出我们将一个简单代码进行控制流平坦化的方法步骤**是什么吗？
5. 请尝试将刚刚请大家绘制控制流图的练习代码进行平坦化，给出你的代码，请自己验证修改后代码的正确性。

</div>
</details>

