# 第5章 指针与数组

> 指针式一种保存变量地址的变量

```c
// 一元运算符 & 可用于取一个对象的地址

p = &c;
```


```c
// 一元运算符 * 是间接寻址或间接引用运算符

int x = 1, y = 2, z[10];
int *ip;        // ip 是指向int类型的指针

ip = &x;        // ip 现在指向 x
y = *ip;        // y 的值现在是1
*ip = 0;        // x 的值现在是0
ip = &z[0]      // ip 现在指向z[0]
```

## 5.2 指针与函数参数

```c
void swap(int x, int y)
{
    int temp;

    temp = x;
    x = y;
    y = temp;
}
swap(a, b); // 无法达到交换值的目的
// 由于参数传递采用传值方式，因此该函数仅交换了a和b的副本的值
```

```c
void swap(int *px, int *py)
{
    int temp;
    temp = *px;
    *px = *py;
    *py = temp;
}

swap(&a, &b);
```

## 5.3 指针与数组

```c
// 返回字符串s的长度
int strlen(char *s)
{
    int n;

    for (n = 0; *s != '\0'; s++)
        n++;

    return n;
}
```


## 5.4 地址算术运算

```c
#define ALLOCSIZE 10000  // 可用空间大小

static char allocbuf[ALLOCSIZE];    // alloc使用的存储区
static char *allocp = allocbuf;     // 下一个空闲位置

char *alloc(int n)
{
    // 返回指向n个字符的指针
    if (allocbuf + ALLOCSIZE - allocp >= n) {
        // 有足够的空间
        allocp += n;
        return allocp - n;  // 分配前的指针p
    } else
        return 0;
}

void afree(char *p) {
    // 释放p指向的存储区
    if (p >= allocbuf && p < allocbuf + ALLOCSIZE)
        allocp = p;
}
```

## 5.5 字符指针与函数

## 5.6 指针数组以及指向指针的指针

## 5.7 多维数组

## 5.8 指针数组的初始化

## 5.9 指针与多位数组

## 5.10 命令行参数

## 5.11 指向函数的指针

## 5.12 复杂声明

