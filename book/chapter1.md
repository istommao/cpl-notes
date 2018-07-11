# 第一章 导言

- 入门
- 变量与算术表达式
- for语句
- 符号常量
- 字符输入/输出
    - 文件复制
    - 字符计数
    - 行计数
    - 单词计数
- 数组
- 函数
- 参数 传值调用
- 字符数组
- 外部变量与作用域

## 1.1 入门

`打印 hello, world`

```c
#include <stdio.h>

int main()
{
    printf("hello, world\n");
}
```

## 1.2 变量与算术表达式

`华氏度与摄氏度公式`
C = (5/9)(F - 32)

```c
#include <stdio.h>

int main()
{
    int fahr, celsius;
    int lower, upper, step;

    lower = 0;
    upper = 300;
    step = 20;

    fahr = lower;
    while (fahr <= upper) {
        celsius = 5 * (fahr - 32) / 9;
        printf("%d\t%d\n", fahr, celsius);
        fahr = fahr + step;
    }
}
```

`浮点数版本`


```c
#include <stdio.h>

int main()
{
    float fahr, celsius;
    int lower, upper, step;

    lower = 0;
    upper = 300;
    step = 20;

    fahr = lower;
    while (fahr <= upper) {
        celsius = (5.0/9.0) * (fahr - 32.0);
        printf("%3.0f\t%6.1f\n", fahr, celsius);
        fahr = fahr + step;
    }
}
```

- %o 表示八进制
- %X 表示十六进制
- %c 表示字符
- %s 表示字符串
- %% 表示百分号本身

## 1.3 for语句

```c
#include <stdio.h>

int main()
{
    int fahr;
    for (fahr = 0; fahr <= 300; fahr = fahr + 20)
        printf("%3d %6.1f\n", fahr, (5.0 / 9.0) * (fahr - 32));
}
```

## 1.4 符号常量

```c
#include <stdio.h>

#define LOWER 0
#define UPPER 300
#define STEP 20

int main()
{
    int fahr;
    for (fahr = LOWER; fahr <= UPPER; fahr = fahr + STEP)
        printf("%3d %6.1f\n", fahr, (5.0 / 9.0) * (fahr - 32));
}
```

## 1.5 字符输入/输出

最简单的字符输入/输出就是使用
标准库提供的 getchar和putchar 两个函数

## 1.5.1 文件复制

```c
#include <stdio.h>

int main()
{
    int c;
    c = getchar();
    while (c != EOF) {
        putchar(c);
        c = getchar();
    }
}
```

```c
// 精简版
#include <stdio.h>

int main()
{
    int c;
    c = getchar();
    while ((c = getchar()) != EOF)
        putchar(c);
}
```

## 1.5.2 字符计数

```c
#include <stdio.h>

int main()
{
    long nc;
    nc = 0;

    while (getchar() != EOF)
        ++nc;
    printf("%ld\n", nc);
}
```

## 1.5.3 行计数

```c
#include <stdio.h>

int main()
{
    int c, nl;

    nl = 0;
    while ((c = getchar()) != EOF)
        if (c == '\n')
            ++nl;
    printf("%d\n", nl);
}
```

## 1.5.4 单词计数

```c
#include <stdio.h>

#define IN 1
#define OUT 0

int main()
{
    int c, nl, nw, nc, state;

    state = OUT;
    nl = nw = nc = 0;
    while ((c = getchar()) != EOF) {
        ++nc;
        if (c == '\n')
            ++nl;
        if (c == ' ' || c == '\n' || c == '\t')
            state = OUT;
        else if (state == OUT) {
            state = IN;
            ++nw;
        }
    }
    printf("%d %d %d\n", nl, nw, nc);
}
```

## 1.6 数组

```c
#include <stdio.h>

int main()
{
    int c, i, nwhite, nother;
    int ndigit[10];

    nwhite = nother = 0;

    for (i = 0; i < 10; ++i)
        ndigit[i] = 0;

    while ((c = getchar()) != EOF)
        if (c >= '0' && c <= '9')
            ++ndigit[c - '0'];
        else if (c == ' ' || c == '\n' || c == '\t')
            ++nwhite;
        else
            ++nother;

    printf("digits =");
    for (i = 0; i < 10; ++i)
        printf(" %d", ndigit[i]);
    printf(", white space = %d, other = %d\n", nwhite, nother);
}
```

## 1.7 函数

```c
#include <stdio.h>

int power(int m, int n);

int main()
{
    int i;

    for (i = 0; i < 10; ++i)
        printf("%d %d %d\n", i, power(2, i), power(-3, i));

    return 0;
}

int power(int base, int n)
{
    int i, p;

    p = 1;
    for (i = 1; i <= n; ++i)
        p = p * base;

    return p;
}
```

