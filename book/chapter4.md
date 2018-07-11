# 第4章 函数与程序结构


# 4.10 递归

```c
#include <stdio.h>

void printd(int n)
{
    if (n <0) {
        putchar('-');
        n = -n;
    }
    if (n / 10)
        printd(n / 10);
    putchar(n % 10 + '0');
}

int main()
{
    printd(1024);
}
```

## 4.11 C预处理器

## 4.11.2 宏替换

```c
#define 名字 替换文本
```

`示例`

```c
#define forever for (;;)

#define max(A, B) ((A) > (B) ? (A) : (B))
```
