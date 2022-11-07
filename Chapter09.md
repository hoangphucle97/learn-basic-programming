# Function
## The problems.
### Three commands to enter a, b, c > 0
```sh
do {
printf(“Nhap mot so nguyen duong: ”);
scanf(“%d”, &a);
} while (a <= 0);
do {
printf(“Nhap mot so nguyen duong: ”);
scanf(“%d”, &b);
} while (b <= 0);
do {
printf(“Nhap mot so nguyen duong: ”);
scanf(“%d”, &c);
} while (c <= 0);
```
### Three commands to calculate s1 = a!, s2 = b!, s3 = c!.
``` sh
{ Tính s1 = a! = 1 * 2 * … * a }
s1 = 1;
for (i = 2; i <= a ; i++)
s1 = s1 * i;
{ Tính s2 = b! = 1 * 2 * … * b }
s2 = 1;
for (i = 2; i <= b ; i++)
s2 = s2 * i;
{ Tính s3 = c! = 1 * 2 * … * c }
s3 = 1;
for (i = 2; i <= c ; i++)
s3 = s3 * i;
```
### Solution => Write once and use many times.
#### Input command, with n = a, b, c.
``` sh 
do {
printf(“Nhap mot so nguyen duong: ”);
scanf(“%d”, &n);
} while (n <= 0);
```
#### The command to calculate the general factorial, n = a, b, c.
``` sh
{ Tính s = n! = 1 * 2 * … * n }
s = 1;
for (i = 2; i <= n ; i++)
s = s * i;
```
## Function
### Syntax
``` sh
<kiểu trả về> <tên hàm>([<danh sách tham số>])
{
<các câu lệnh>
[return <giá trị>;]
}
```
- Example:
```sh
void NhapXuatTong()
{
int x, y;
printf(“Nhap 2 so nguyen: ”);
scanf(“%d%d”, &x, &y);
printf(“%d cong %d bang %d”, x, y, x + y);
}
```
### Scope of variables and functions.
- Global variables: declare inside and outside all functions (including main function) and affect the entire program.
- Local variable: declared within a function or block {} and has effect only within the function or block itself (including its sub-blocks). The local variable will be deleted from memory at the end of the block declaring it.
 #### Note: It is common practice to place the function header/prototype above main and the function definition below main.
 ```sh
void XuatTong(int x, int y); // prototype
void main()
{
…
}
void XuatTong(int x, int y)
{
printf(“%d cong %d bang %d”, x, y, x + y);
}
```
## Ways to pass arguments
### Call by Address
- Pass arguments to the function in the form of an address (con
pointer).
- Do not pass a value for this parameter.
- Used when there is a need to change the value of the parameter after executing the function.
```sh
void TruyenDiaChi(int *x)
{
…
*x++;
}
```
### Call by Value
- Pass arguments to the function as values.
- Can pass constants, variables, expressions but
the function will only receive the value.
- Used when there is no need to change the value of the parameter after executing the function.
```sh
void TruyenGiaTri(int x)
{
…
x++;
}
```
### Note
- Within a function, parameters can be passed in many ways.
```sh
void HonHop(int x, int &y)
{
…
x++;
y++;
}
```
- Using a reference is a way to return a value to a program.
```sh
int TinhTong(int x, int y)
{
return x + y;
}
void TinhTong(int x, int y, int &tong)
{
tong = x + y;
}
void TinhTongHieu(int x, int y, int &tong, int &hieu)
{
tong = x + y; hieu = x – y;
}
```
## Function call
- Call the name of the function and pass the arguments (constants, variables, expressions) to the parameters in the order declared in the function.
- These variables or values are separated by a ,
- These arguments are enclosed in parentheses ().
    **<function name> (<argument 1>… , <argument n>); **
```sh
void main()
{
int n = 9;
XuatTong(1, 2);
XuatTong(1, n);
TinhTong(1, 2);
int tong = TinhTong(1, 2);
TruyenGiaTri(1);
TruyenGiaTri(n);
}
```
## Recursive.
- A subroutine can call a chapter other subroutine.
- If calling itself, it is called recursion.
- This number of calls must have a limit (stops).
- Example:
```sh
int GiaiThua(int n)
{
if (n == 0)
return 1;
else
return GiaiThua(n – 1) * n;
}
int GiaiThua(int n)
{
if (n > 0)
return GiaiThua(n – 1) * n;
else
return 1;
}
```

