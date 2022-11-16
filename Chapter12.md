# Chapter 12: Pointer Data (Basic).
## Declare pointer.
- Like any other variable, the pointer variable you want to use also needs to be declared.
    **<kiểu dữ liệu> *<tên biến con trỏ>;**
```sh
char *ch1, *ch2;
int *p1, p2;
```
    + ch1 and ch2 are pointer variables, pointing to char (1 byte) memory.
    + p1 is a pointer variable, pointing to an int (4 bytes) memory area and p2 is a normal int variable.
- Use typedef keyword.
    **typedef <kiểu dữ liệu> *<tên kiểu con trỏ>;**
    **<tên kiểu con trỏ> <tên biến con trỏ>;**
```sh
typedef int *pint;
int *p1;
pint p2, p3;
```
    + Reduce confusion when first coming into contact with the pointer.
    + But easy to confuse with normal variables.
## NULL pointer.
### Concept.
- A NULL pointer is a pointer that does not point anywhere.
- Different from uninitialized pointer.
```sh
int n;
int *p1 = &n;
int *p2; // unreferenced local variable
int *p3 = NULL;
```
### Initialize pointer type.
- When newly declared, the pointer variable is placed at a certain address (not known in advance).
    + contains undefined value
    + points to an unknown memory area.
- Put the address of the variable into the pointer (& operator).
    **<tên biến con trỏ> = &<tên biến>;**
```sh
int a, b;
int *pa = &a, *pb;
pb = &b;
```
### Using pointers.
- Pointer contains an integer indicating the address.
- The memory it points to, using the * operator.
```sh
int a = 5, *pa = &a;
printf(“%d\n”, pa); // Giá trị biến pa
printf(“%d\n”, *pa); // Giá trị vùng nhớ pa trỏ đến
printf(“%d\n”, &pa); // Địa chỉ biến pa
```
## Ways to pass arguments.
### Value transmission.
```sh
#include <stdio.h>
void hoanvi(int x, int y);
void main()
{
int a = 5; b = 6;
hoanvi(a, b);
printf(“a = %d, b = %d”, a, b);
}
void hoanvi(int x, int y)
{
int t = x; x = y; y = t;
}
```
### Address transmission (pointer).
```sh
#include <stdio.h>
void hoanvi(int *x, int *y);
void main()
{
int a = 2912; b = 1706;
hoanvi(&a, &b);
printf(“a = %d, b = %d”, a, b);
}
void hoanvi(int *x, int *y)
{
int t = *x; *x = *y; *y = t;
}
```
### Reference transmission (C++).
```sh
#include <stdio.h>
void hoanvi(int &x, int &y);
void main()
{
int a = 2912; b = 1706;
hoanvi(a, b);
printf(“a = %d, b = %d”, a, b);
}
void hoanvi(int &x, int &y)
{
int t = x; x = y; y = t;
}
```
    