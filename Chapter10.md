# One-dimensional array.
## Array data.
- A structured data type defined by the programmer.
- Represents a sequence of variables of the same type. For example: sequence of integers, sequence of characters...
- The size is determined at the time of declaration and never changes.
The C programming language always assigns a contiguous block of memory to an array variable.
## Declare array variables.
### Explicit.
```sh
<kiểu cơ sở> <tên biến mảng>[<số phần tử>];
<kiểu cơ sở> <tên biến mảng>[<N1>][<N2>]…[<Nn>];
```
#### Note
- Must specify a specific <number of elements> (constants) when declaring.
- Multidimensional array: <total number of elements> = N1*N2* *Nn
- Memory usage = <total number of elements>*sizeof(<base type>).
- Memory usage must be less than 64KB (65536 Bytes).
- A continuous sequence with index from 0 to <total number of elements>-1.
### Unexplicit
```sh
typedef <kiểu cơ sở> <tên kiểu mảng>[<số phần tử>];
typedef <kiểu cơ sở> <tên kiểu mảng>[<N1>]…[<Nn>];
<tên kiểu mảng> <tên biến mảng>;
```
## The number of elements of the array.
- The number of elements must be determined at the time of declaration, without using variables or constants.
``` sh
int n1 = 10; int a[n1];
const int n2 = 20; int b[n2];
```
- You should use #define preprocessor directive to define array element meaning.
``` sh
#define n1 10
#define n2 20
int a[n1]; // <=> int a[10];
int b[n1][n2]; // <=> int b[10][20];
```
## Array data assignment.
- Do not use normal assignment but must assign directly between corresponding elements.
- <biến mảng đích>[<chỉ số thứ i>] = <giá trị>;
```sh
#define MAX 3
typedef int MangSo[MAX];
MangSo a = {1, 2, 3}, b;
b = a; // Sai
for (int i = 0; i < 3; i++) b[i] = a[i];
```
### Some common mistakes.
```sh
The declaration does not specify the number of elements
   int a[ ]; => int a[100];
The number of elements related to the variable or constant
  int n1 = 10; int a[n1]; => int a[10];
  const int n2 = 10; int a[n2]; => int a[10];
Initialization separate from declaration
  int a[4]; a = {2912, 1706, 1506, 1904};
    => int a[4] = {2912, 1706, 1506, 1904};
Invalid array index
  int a[4];
  a[-1] = 1; a[10] = 0;
  ```
## Pass array to function.
### Pass array to function.
- Array-type parameters in function declarations are the same as array variable declarations.
- The array parameter passed to the main function is the address of the first element of the array (the number of elements can be dropped or you can use pointers and the array can be changed after executing the function).
```sh
void SapXepTang(int a[]);
void SapXepTang(int *a);
```
- Number of elements actually passed to another variable.
```sh
void SapXepTang(int a[100], int n);
void SapXepTang(int a[], int n);
void SapXepTang(int *a, int n);
```
### Function call
```sh
void NhapMang(int a[], int &n);
void XuatMang(int a[], int n);
void main()
{
int a[100], n;
NhapMang(a, n);
XuatMang(a, n);
}
```
## Some conventions.
### Number of elements.
**#define MAX 100**
### Functions.
- Function void HoanVi(int &x, int &y): permutates the value of two integers.
- Function int LaSNT(int n): check if a number is prime. Returns 1 if n is prime, otherwise returns 0.
```sh
void HoanVi(int &x, int &y)
{
int tam = x; x = y; y = tam;
}
int LaSNT(int n)
{
int i, dem = 0;
for (i = 1; i <= n; i++)
if (n%i == 0)
dem++;
if (dem == 2)
return 1;
else return 0;
}
```
## Array Input Function.
```sh
void NhapMang(int a[], int &n)
{
printf(“Nhap so luong phan tu n: ”);
scanf(“%d”, &n);
for (int i = 0; i < n; i++)
{
printf(“Nhap phan tu thu %d: ”, i);
scanf(“%d”, &a[i]);
}
}
```
## Array Output Function.
```sh
void XuatMang(int a[], int n)
{
printf(“Noi dung cua mang la: ”);
for (int i = 0; i < n; i++)
printf(“%d ”, a[i]);
printf(“\n”);
}
```
## Search function (using while).
```sh
int TimKiem(int a[], int n, int x)
{
int vt = 0;
while (vt < n && a[vt] != x)
vt++;
if (vt < n)
return vt;
else
return -1;
}
```
## Search function (using for).
```sh
int TimKiem(int a[], int n, int x)
{
for (int vt = 0; vt < n; vt++)
if (a[vt] == x)
return vt;
return -1;
}
```
