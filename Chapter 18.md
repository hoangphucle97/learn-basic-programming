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