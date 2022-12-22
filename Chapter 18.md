# Chapter 18: ADVANCED FUNCTION (Part 2).
## Parameter.
### Declare.
```sh
<kiểu trả về> <tên hàm>(<dsts biết trước>, …)
{
…
}
```
### Meaningful.
- The function has an unknown number of parameters and is usually of the same type (cannot be char, unsigned char, float).
- Must have at least 1 known parameter.
- Parameters ... put at the end.
### Example.
```sh
void XuatTong1(char *msg, int n, …)
{
// Các lệnh ở đây
}
void XuatTong2(char *msg, …)
{
// Các lệnh ở đây
}
int Tong(int a, …)
{
// Các lệnh ở đây
}
```
### Use the following styles and macros (stdarg.h).
- va_list : data type containing the parameters contained in ...
- va_start(va_list ap, lastfix) : macro sets ap to the first parameter in … with lastfix being the last fixed parameter name.
- type va_arg(va_list ap, type) : the macro returns the parameter of the next type.
- va_end(va_list ap) : a macro that helps the function return a value "normally".
### Example.
```sh
#include <stdarg.h>
void XuatTong1(char *msg, int n, …)
{
va_list ap;
va_start(ap, n); // ts cố định cuối cùng
int value, s = 0;
for (int i=0; i<n; i++)
{
value = va_arg(ap, int);
s = s + value;
}
va_end(ap);
printf(“%s %d”, msg, s);
}
```
## Function template.
### Concept.
- Write a single function that can be used for many different data types.
### Syntax.
**tempate <ds mẫu tham số> <khai báo hàm>**
### Example.
```sh
template <class T>
T min(T a, T b)
{
if (a < b)
return a;
return b;
}
void main()
{
int a = 2912, b = 1706;
int m = min<int>(a, b);
printf(“So nho nhat la %d”, m);
}
```
## Function overloading.
### Concept.
- Function with the same name but with different input or output parameters.
- The function prototype (prototype) when omitting the parameter name must be different.
- Allows the user to choose the most convenient method to do the job.
### Example.
- Import arrays in several ways.
```sh
void Nhap(int a[], int &n)
{
// Nhập n rồi nhập mảng a
}
void Nhap(int a[], int n)
{
// Nhập mảng a theo n truyền vào
}
int Nhap(int a[])
{
// Nhập n, nhập mảng a rồi trả n về
}
```
- Assign a value to PHANSO.
```sh
void Gan(PHANSO &ps, int tu, int mau)
{
ps.tu = tu;
ps.mau = mau;
}
void Gan(PHANSO &ps, int tu)
{
ps.tu = tu;
ps.mau = 1;
}
```
### Ambiguity.
- Due to the type conversion.
```sh
void f(unsigned char c)
{
printf(“%d”, c);
}
void f(char c)
{
printf(“%c”, c);
}
void main()
{
f(„A‟); // char
f(65); // ???
}
```
- Due to the use of references.
```sh
int f(int a, int b)
{
return a + b;
}
int f(int a, int &b)
{
return a + b;
}
void main()
{
int x = 1, y = 2;
printf(“%d”, f(x, y)); // ???
}
```
- Due to the default parameter usage.
```sh
int f(int a)
{
return a*a;
}
int f(int a, int b = 0)
{
return a*b;
}
void main()
{
printf(“%d\n”, f(2912, 1706));
printf(“%d\n”, f(2912)); //???
}
```
