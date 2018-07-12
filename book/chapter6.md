# 第6章 结构

## 6.1 结构的基本知识

```c
struct point {
    int x;
    int y;
};
```

`结构可以嵌套`

```c
struct rect {
    struct point pt1;
    struct point pt2;
};
```

## 6.2 结构与函数

```c
struct point makepoint(int x, int y)
{
    struct point temp;

    temp.x = x;
    temp.y = y;
    return temp;
};
```

## 6.3 结构数组

## 6.4 指向结构的指针


## 6.5 自引用结构

```c
struct tnode {
    char *word;
    int count;
    struct tnode *left;
    struct tnode *right;
};
```

## 6.6 表查询

## 6.7 类型定义 (typedef)

```c
typedef int Length;

Length len, maxlen;
Lenght *lengths[];

typedef char *String;

String p, lineptr[MAXLINES], alloc(int);
int strcmp(String, String);
p = (String)malloc(100);
```

