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


### 练习5：输出一个数的所有素因数（for循环嵌套for循环语句）

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
