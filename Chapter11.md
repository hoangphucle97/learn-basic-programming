# TWO-DIMENSIONAL ARRAY.
## Declare two dimensional array.
- Syntax: **typedef <kiểu cơ sở> <tên kiểu>[<N1>][<N2>]**
- Example: typedef int MaTran[3][4];
### Explicit: 
**<kiểu cơ sở> <tên biến>[<N1>][<N2>];**
```sh
int a[10][20], b[10][20];
int c[5][10];
int d[10][20];
```
### Unexplicit: 
**typedef <kiểu cơ sở> <tên kiểu>[<N1>][<N2>];**
**<tên kiểu> <tên biến>;**
**<tên kiểu> <tên biến 1>, <tên biến 2>;**
```sh
typedef int MaTran10x20[10][20];
typedef int MaTran5x10[5][10];
MaTran10x20 a, b;
MaTran11x11 c;
MaTran10x20 d;
```
## Access to an element.
### Through the index.
**<tên biến mảng>[<giá trị cs1>][<giá trị cs2>]**
### Example.
```sh
int a[3][4];
- Valid: a[0][0], a[0][1], …, a[2][2], a[2][3].
- Unvalid a[-1][0], a[2][4], a[3][3].
```
## Array data assignment.
- Do not use normal assignment but must assign directly between elements.
 **<biến mảng đích>[<giá trị cs1>][giá trị cs2] = <giá trị>;**
- Example:
```sh
int a[5][10], b[5][10];
b = a; // Sai
int i, j;
for (i = 0; i < 5; i++)
for (j = 0; j < 10; j++)
b[i][j] = a[i][j];
```
## Pass array to function.
### Pass array to function
- Array-type parameters in function declarations are the same as array variable declarations.
    **void NhapMaTran(int a[50][100]);**
- The array type parameter passed to the main function is the address of the first element of the array (The number of 2nd dimension elements or pointers can be dropped, and the Array can change contents after the function is executed).
    **void NhapMaTran(int a[][100]);**
    **void NhapMaTran(int (*a)[100]);**
- Number of elements actually passed to another variable.
    **void XuatMaTran(int a[50][100], int m, int n);**
    **void XuatMaTran(int a[][100], int m, int n);**
    **void XuatMaTran(int (*a)[100], int m, int n);**
### Function call.
```sh
void NhapMaTran(int a[][100], int &m, int &n);
void XuatMaTran(int a[][100], int m, int n);
void main()
{
int a[50][100], m, n;
NhapMaTran(a, m, n);
XuatMaTran(a, m, n);
}
```
