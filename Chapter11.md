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
## Some conventions.
### Data types.
```sh
define MAXD 50
define MAXC 100
```
### Subprograms.
- Function void HoanVi(int x, int y): permutates the value of two integers.
```sh
void HoanVi(int &x, int &y)
{
int tam = x; x = y; y = tam;
}
```
- Function int LaSNT(int n): check if a number is prime. Returns 1 if n is prime, otherwise returns 0.
```sh
int LaSNT(int n)
{
int i, dem = 0;
for (i = 1; i <= n; i++)
if (n%i == 0)
dem++;
if (dem == 2)
return 1;
return 0;
}
```
## Enter matrix.
### Request.
- Allow to enter array a, m rows, n columns.
### Idea.
- Given a two-dimensional array with maximum rows of MAXD, maximum number of columns is MAXC.
- Enter the actual number of m, n elements of each dimension.
- Enter each element from [0][0] to [m-1][n-1].
## Matrix input function.
```sh
void NhapMaTran(int a[][MAXC], int &m, int &n)
{
printf(“Nhap so dong, so cot cua ma tran: ”);
scanf(“%d%d”, &m, &n);
int i, j;
for (i=0; i<m; i++)
for (j=0; j<n; j++)
{
printf(“Nhap a[%d][%d]: ”, i, j);
scanf(“%d”, &a[i][j]);
}
}
```
## Export matrix.
### Request.
- Allow to enter array a, m columms, n rows.
### Idea.
- Outputs the value of each element of a 2-dimensional array from row 0 to row m-1, each row outputs the value of column 0 to column n-1 on that row.
## Matrix Output Function.
```sh
void XuatMaTran(int a[][MAXC], int m, int n)
{
int i, j;
for (i=0; i<m; i++)
{
for (j=0; j<n; j++)
printf(“%d ”, a[i][j]);
printf(“\n”);
}
}
```
## Search for an element in a matrix.
### Request.
- Find if element x is in a matrix of size m x n or not?.
### Idea.
- Traverse each part of the matrix a. If the element under consideration is x, then return yes (1), otherwise return no (0).
## Search function.
```sh
int TimKiem(int a[][MAXC], int m, int n, int x)
{
int i, j;
for (i=0; i<m; i++)
for (j=0; j<n; j++)
if (a[i][j] == x)
return 1;
return 0;
}
```
## Check array properties.
### Request.
- Given a matrix of size m x n. Is matrix a a matrix of all prime numbers?
### Idea.
- Method 1: Count the number of primes of the matrix. If this number is exactly mxn, then the matrix is all prime.
```sh
int KiemTra_C1(int a[][MAXC], int m, int n)
{
int i, j, dem = 0;
for (i=0; i<m; i++)
for (j=0; j<n; j++)
if (LaSNT(a[i][j]==1))
dem++;
if (dem == m*n)
return 1;
return 0;
}
```
- Method 2: Count the number of non-prime numbers of the matrix. If this number is zero then the matrix is all prime.
```sh
int KiemTra_C2(int a[][MAXC], int m, int n)
{
int i, j, dem = 0;
for (i=0; i<m; i++)
for (j=0; j<n; j++)
if (LaSNT(a[i][j]==0))
dem++;
if (dem == 0)
return 1;
return 0;
}
```
- Method 3: Find if any element is not prime. If so, the matrix is not all prime.
```sh
int KiemTra_C3(int a[][MAXC], int m, int n)
{
int i, j, dem = 0;
for (i=0; i<m; i++)
for (j=0; j<n; j++)
if (LaSNT(a[i][j]==0))
return 0;
return 1;
}
```
## Sum the elements.
### Request.
- Given matrix a, size mxn. Sum of the above elements:
    + Row d, column c
    + Main diagonal, minor diagonal (square matrix).
    + The top/bottom half of the main diagonal (square matrix).
    + The upper/lower half of the secondary diagonal (square matrix).
### Idea.
- Browse the matrix and add up the elements with coordinates (rows, columns) that meet the requirements.
## Line sum function.
```sh
int TongDong(int a[][MAXC], int m, int n, int d)
{
int j, tong;
tong = 0;
for (j=0; j<n; j++) // Duyệt các cột
tong = tong + a[d][j];
return tong;
}
```
## Sum function on column.
```sh
int TongCot(int a[][MAXC], int m, int c)
{
int i, tong;
tong = 0;
for (i=0; i<m; i++) // Duyệt các dòng
tong = tong + a[i][c];
return tong;
}
```
## Main diagonal sum function.
```sh
int TongDCChinh(int a[][MAXC], int n)
{
int i, tong;
tong = 0;
for (i=0; i<n; i++)
tong = tong + a[i][i];
return tong;
}
```
## Sum function on main diagonal.
```sh
int TongTrenDCChinh(int a[][MAXC], int n)
{
int i, j, tong;
tong = 0;
for (i=0; i<n; i++)
for (j=0; j<n; j++)
if (i < j)
tong = tong + a[i][j];
return tong;
}
```
## Sum function under main diagonal.
```sh
int TongTrenDCChinh(int a[][MAXC], int n)
{
int i, j, tong;
tong = 0;
for (i=0; i<n; i++)
for (j=0; j<n; j++)
if (i > j)
tong = tong + a[i][j];
return tong;
}
```
## Sum function on sub diagonal.
```sh
int TongDCPhu(int a[][MAXC], int n)
{
int i, tong;
tong = 0;
for (i=0; i<n; i++)
tong = tong + a[i][n-i-1];
return tong;
}
```
## Find the maximum value of the Matrix.
### Request.
- Given a matrix a, size mxn. Find the maximum value in the matrix a (called max).
### Idea.
- Assume the current max value is the first element value a[0][0].
- Check the remaining elements in turn to update max.
## Function to find Max.
```sh
int TimMax(int a[][MAXC], int m, int n)
{
int i, j, max;
max = a[0][0];
for (i=0; i<m; i++)
for (j=0; j<n; j++)
if (a[i][j] > max)
max = a[i][j];
return max;
}
```
