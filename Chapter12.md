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
## Pointers and one-dimensional arrays.
### One-dimensional arrays.
    **int array[number];**
- The array name array is a pointer constant
  ->The value of this constant cannot be changed.
- The value of array is the address of the first element of the array
-> array == &array[0]
### Pointer to one-dimensional array.
```sh
int array[3], *parray;
parray = array; // Method 1
parray = &array[0]; // Method 2
```
## Arithmetic operations on pointers.
### Addition (increase).
- + n <-> + n * sizeof(<data type>).
- Can use the aggregate operator += or ++.
### Subtraction (decrease).
- - n <-> - n * sizeof(<data type>).
- Can use the aggregate operator -= or --.
### Calculation of the distance between two pointers.
- <data type> *p1, *p2;
- p1 - p2 gives us the distance (in number of elements) between two pointers (of the same type).
### Other math operations.
- Comparison operation: Compares addresses between two children pointer (order of memory cells)
    == !=
    > >=
    < <=
- Cannot perform math operations: * / %.
## Pointers and one-dimensional arrays.
### Access to the nth element of the array.
**array[n] == p[n] == *(p + n)**
### Array input example.
```sh
void main()
{
int a[10], n = 10, *pa;
pa = a; // hoặc pa = &a[0];
for (int i = 0; i<n; i++)
scanf(“%d”, &a[i]);
scanf(“%d”, &pa[i]);
scanf(“%d”, a + i);
scanf(“%d”, pa + i);
scanf(“%d”, a++);
scanf(“%d”, pa++);
}
=> &a[i] <=> (a + i) <=> (pa + i) <=> &pa[i]
```
### Array output example.
```sh
void main()
{
int a[10], n = 10, *pa;
pa = a; // hoặc pa = &a[0];
…
for (int i = 0; i<n; i++)
printf(“%d”, a[i]);
printf(“%d”, pa[i]);
printf(“%d”, *(a + i));
printf(“%d”, *(pa + i));
printf(“%d”, *(a++));
printf(“%d”, *(pa++));
}
=> a[i] <=> *(a + i) <=> *(pa + i) <=> pa[i]
```
### Pass a one - dimensional array to the function.
**Note: The one-dimensional array passed to the function is the address of the first element, not the entire array.**
### The array argument passed to the function.
```sh
void xuat(int a[10], int n)
{
for (int i = 0; i<n; i++)
printf(“%d”, *(a++)); // OK
}
void main()
{
int a[10], n = 10;
for (int i = 0; i<n; i++)
printf(“%d”, *(a++)); // Lỗi
}
```
=> The array argument passed to the function is not a pointer constant.
### Pointers and structs.
- Access in two ways.
    **<tên biến con trỏ cấu trúc>-><tên thành phần>**
    **(*<tên biến con trỏ cấu trúc>).<tên thành phần>**
- Example
```sh
typedef struct
{
int tu, mau;
} PHANSO;
PHANSO ps1, *ps2 = &ps1; // ps2 là con trỏ
ps1.tu = 1; ps1.mau = 2;
ps2->tu = 1; ps2->mau = 2;
<=> (*ps2).tu = 1; (*ps2).mau = 2;
```