# C语言-条件语句

Author: [sikesibian](https://github.com/sikesibian)

* TOC
{:toc}

> 在完成本节之前，建议先完成C语言基础语法、C语言赋值语句、C语言变量与运算符、C语言条件语句的学习。

## 1. if语句

### 练习1：判断奇偶（认识`if(-else)`语句）

<details>
<summary>输入一个整数，判断其是否为偶数。</summary>
<div markdown="1">

输入数据范围：`[-10000, 10000]`

输入输出样例：
```
输入：
5
输出：
5 is odd
```
```
输入：
6
输出：
6 is even
```
</div>
</details>

### 练习2：判断闰年（复杂条件判断）

<details>
<summary>输入一个年份，判断其是否为闰年。</summary>
<div markdown="1">

输入数据范围：`[1900, 2100]`

输入输出样例：
```
输入：
2000
输出：
2000 is leap year.
```
```
输入：
2001
输出：
2001 is not leap year.
```
提示：
1. 闰年的判断条件是：能被4整除但不能被100整除，或者能被400整除。
2. `%`表示取余，如`5%2=1`。
3. `&&`表示逻辑与，如`(5>3)&&(5<7)`为真。

</div>
</details>

### 练习3：学生成绩录入系统（`if`语句的嵌套）

<details>
<summary>给出一个C语言程序，要求用户输入一个学生的成绩。根据输入的成绩，使用if语句嵌套判断学生的成绩等级，并输出对应的等级。</summary>
<div markdown="1">

其中成绩等级划分如下：

- 90分及以上为A级，如果成绩为100分，则输出A+
- 80分至89分为B级
- 70分至79分为C级
- 60分至69分为D级
- 60分以下为F级

输入数据范围：`[-100, 100]`的整数

输入输出样例：
```
输入：
85
输出：
B
```
```
输入：
-10
输出：
Invalid input, please input a number between 0 and 100.
```

提示：
1. C语言中不存在连续的不等式，如要表示一个范围，可以使用`>=`和`<=`两个条件与起来。
2. 连续的`if`条件可以嵌套，注意要遵守缩进规则。一种常见的嵌套方式如下所示（又称不完整的嵌套，这种方式将分段的条件**平坦化**）：
```c
if(a > 1){
    printf("a is bigger than 1\n");
} else if(0 < a && a <= 1){
    printf("a is smaller than 1 while bigger than 0\n");
} else if (a == 0) {
    printf("a is equal to 0\n");
} else {
    printf("a is smaller than 0\n");
}
```
</div>
</details>

### 练习4：篮球队的正式招新（卫语句）

<details>
<summary>卫语句阐释</summary>
<div markdown="1">

卫语句（Guard Clause）是一种编程模式，它通过提前退出函数或方法来减少嵌套。在条件判断中，如果某个条件不满足，就立即返回或跳过后续的代码。这种方式可以使代码更加清晰和易于理解。

观察下面这段代码：
```c
# include <stdio.h>

int main() {
    int x, y, z;
    scanf("%d %d %d", &x, &y, &z);
    if (x > 0){
        if (y > 0) {
            if (z > 0){
                printf("x, y, z are all positive\n");
            }
            else {
                printf("x, y are positive but z is not\n");
            }
        }
        else {
            printf("x is positive but y is not\n");
        }
    }
    else {
        printf("x is not positive\n");
    }
    return 0;
}

```

可以把上面的代码拆分成下面这样：

```c
# include <stdio.h>

int main() {
    int x, y, z;
    scanf("%d %d %d", &x, &y, &z);
    if (x <= 0) {
        printf("x is not positive\n");
        return 0;
        // 提前返回，不再执行下面的代码
    }
    if (y <= 0) {
        printf("x is positive but y is not\n");
        return 0;
        // 提前返回，不再执行下面的代码
    }
    if (z <= 0) {
        printf("x, y are positive but z is not\n");
        return 0;
        // 提前返回，不再执行下面的代码
    }
    printf("x, y, z are all positive\n");
    return 0;
}
```

可以看到卫语句中，如果某个条件不满足，就直接返回，不再执行后面的代码。我们从上述代码就可以看到**卫语句的优点**：
- **提高代码的可读性**：通过减少嵌套，使得代码结构更加清晰，易于理解。
- **减少错误**：较少的嵌套可以减少因错误条件判断顺序导致的错误。
- **提高代码的维护性**：当需要修改条件或添加新的条件时，更容易进行修改。

</div>
</details>

<details>
<summary>练习：请将下述代码更改为一个卫语句版本</summary>
<div markdown="1">

```c
#include <stdio.h>

int main() {
    int age, height;
    char hasCompletedTraining;

    printf("The age of the student:");
    scanf("%d", &age);
    printf("The height of the student (centimeters):");
    scanf("%d", &height);
    printf("Did the student complete the basic basketball training? (Y/N)");
    scanf(" %c", &hasCompletedTraining); // 在%c前面有一个空格，用来跳过任何空白字符

    if (age >= 14) {
        if (height >= 170) {
            if (age < 18) {
                if (hasCompletedTraining == 'Y') {
                    printf("This student can join the basketball team.");
                } else {
                    printf("However, the student cannot join the basketball team without basic training.");
                }
            } else {
                printf("This student can join the basketball team.");
            }
        } else {
            printf("The student's height is too low, he cannot join the basketball team.");
        }
    } else {
        printf("The student's age is too low, he cannot join the basketball team.");
    }

    return 0;
}
```
</div>
</details>

## 2. switch语句

<details>
<summary>switch语句阐释</summary>
<div markdown="1">

switch语句是一种选择语句，它根据一个或多个条件判断，执行相应的代码块。它与if语句相比，具有更简洁的语法和更清晰、更易读的代码结构。

`switch`语句的基本格式如下：

```c
switch(expression) {
    case value1:
        statement1;
        break;
    case value2:
        statement2;
        break;
    ...
    default:
        statementN;
        break;
}
```

提醒一些注意事项：
1. 如果没有匹配的`case`，则执行`default`中的代码。
2. 在每个`case`语句中，**必须包含`break`语句，否则会继续执行下一个`case`中的语句（当然这也可以作为一个技巧）**。
3. 同一个`switch`语句中，`case`的值必须是常量表达式，并且不能是变量，而**一个`case`中可能有多个值，用逗号隔开即可**。
</div>
</details>

### 练习5：月份天数查询（`switch`语句的基本使用）

<details>
<summary>请给出一个C语言程序，输入一个年份和一个月份，输出该月份对应的天数。</summary>
<div markdown="1">

数据范围：`1900 <= year <= 2024`，`1 <= month <= 12`

输入输出样例：
```
输入：
2023 2
输出：
28
```
</div>
</details>

### 练习6：喵喵喵！（`case`穿透）

<details>
<summary>使用`case`穿透的效果，简化C语言程序</summary>
<div markdown="1">

前面提到，在`switch`语句中，如果没有匹配的`case`，则执行`default`中的代码。但是，如果在某个`case`中，没有包含`break`，则后续的`case`中的代码也会被执行。我们有时或许可以利用这样的特性，来简化代码。

请你使用`case`穿透的效果，简化下述C语言程序：

```c
#include <stdio.h>

int main() {
    int x;
    scanf("%d", &x);
    switch(x) {
        case 1:
            printf(" /  O  \\ \n");
            break;
        case 2:
            printf(" `>>x<<´  \n");
            printf(" /  O  \\ \n");
            break;
        case 3:
            printf("( > º < ) \n");
            printf(" `>>x<<´  \n");
            printf(" /  O  \\ \n");
            break;
        case 4:
            printf(" / @ @ \\ \n");
            printf("( > º < ) \n");
            printf(" `>>x<<´  \n");
            printf(" /  O  \\ \n");
            break;
        default:
            printf("  |\\_/|  \n");
            printf(" / @ @ \\ \n");
            printf("( > º < ) \n");
            printf(" `>>x<<´  \n");
            printf(" /  O  \\ \n");
            break;
    }
    return 0;
}
```
</div>
</details>

## 3. 三目运算符

<details>
<summary>三目运算符阐释</summary>
<div markdown="1">

三目运算符（Ternary Operator）也称为条件运算符，它允许在条件为真时返回一个值，否则返回另一个值。其基本使用方法如下：
```c
condition ? expression1 : expression2;
```
1. `condition`为真时，返回`expression1`；
2. `condition`为假时，返回`expression2`。
3. `condition`可以是任何表达式，包括变量、常量、函数调用等。

示例：
```c
int x = 5;
int y = (x > 0) ? x : -x;
printf("%d", y);
// 输出：5
```
在上面的例子中，如果`x`大于0，则`y`的值为`x`，否则为`-x`。

</div>
</details>

### 练习7：比大小（三目运算符的简单应用）

<details>
<summary>请给出一个C语言程序，完成一个简易比大小程序。</summary>
<div markdown="1">

请仅使用三目运算符，完成满足下述功能的一个比大小程序：

- 选项1：输入一个整数，输出其绝对值。
- 选项2：输入两个整数，输出它们的最大值。
- 选项3：输入三个整数，输出它们的最小值。

提示：三目运算符也可以嵌套使用。

数据范围：`-1000 <= x <= 1000`

输入第一行为选项数字，第二行为要进行运算的数据。

输入输出样例：
```
输入：
1
-3
输出：
3
```
```
输入
2
5 3
输出
5
```
```
输入
3
2 3 4
输出
2
```
</div>
</details>

### 练习8：少废话，你工资是多少？（ITE表达式）

<details>
<summary>ITE表达式阐释</summary>
<div markdown="1">

ITE表达式，全称是 if-then-else 表达式，是一种在编程语言中常见的条件表达式。它允许根据条件的真假来选择两个值中的一个。C语言中的三目运算符` ? : `就是一个ITE表达式的具体呈现。我们往往可以使用ITE表达式来简化条件判断。

首先看到如下代码：

```c
#include <stdio.h>
int main() {
    int score;
    scanf("%d", &score);
    char grade;
    if (score >= 90) {
        grade = 'A';
    } else if (score >= 80) {
        grade = 'B';
    } else if (score >= 70) {
        grade = 'C';
    } else if (score >= 60) {
        grade = 'D';
    } else {
        grade = 'F';
    }
    printf("Your grade is %c.", grade);
    return 0;
}
```

而如果我们使用ITE表达式，可以简化为：
```c
#include <stdio.h>
int main() {
    int score;
    scanf("%d", &score);
    printf("Your grade is %c.", 
        score >= 90 ? 'A' :
        score >= 80 ? 'B' :
        score >= 70 ? 'C' :
        score >= 60 ? 'D' : 'F'
    );
    return 0;
}
```

可以梳理出上述代码中的逻辑链可视化如下（Y为真，N为假）：
```
    +-------+
    | score |
    +-------+
        | >= 90 ?
   +----+----+
  Y|         |N
 +-v-+       |
 | A |       | >= 80 ?
 +---+  +----+----+
       Y|         |N
      +-v-+       |
      | B |       | >= 70 ?
      +---+  +----+----+
            Y|         |N
           +-v-+       |
           | C |       | >= 60 ?
           +---+  +----+----+
                 Y|         |N
                +-v-+     +-v-+
                | D |     | F |
                +---+     +---+
```

</div>
</details>

<details>
<summary>练习：修改代码，使用ITE表达式来实现条件语句</summary>
<div markdown="1">

练习：请修改下面这个计算一个员工的奖金的程序，将其中的条件语句均使用ITE表达式来完成，其中根据员工的等级和业绩来确定奖金的百分比：

```c
#include <stdio.h>

int main() {
    double salary, bonus = 0.0;
    char performance, level;
    scanf("%lf %c %c", &salary, &performance, &level);
    if (level == 'A') {
        if (performance == 'E') {
            bonus = salary * 0.20;
        } else {
            bonus = salary * 0.15;
        }
    } else if (level == 'B') {
        if (performance == 'E') {
            bonus = salary * 0.15;
        } else {
            bonus = salary * 0.10;
        }
    } else if (level == 'C') {
        if (performance == 'E') {
            bonus = salary * 0.10;
        } else {
            bonus = salary * 0.05;
        }
    } else {
        bonus = salary * 0.05;
    }
    printf("Your bonus is %.2lf.", bonus);
    return 0;
}
```
</div>
</details>





