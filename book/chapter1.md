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

