# Chapter 16: STRUCTURE TYPE DATA.
## Problem
### One student information
- MSSV : string type
- Student name: string type
- NTNS : string type
- Gender: symbol type
-Math, Physics, Chemistry scores: real number type.
### Declare variables to store a student.
- char mssv[7]; // “0012078”
- char hoten[30]; // “Nguyen Van A”
- char ntns[8]; // “29/12/82”
- char phai; // „n‟
- float toan, ly, hoa;// 8.5 9.0 10.0
### Pass a student information to the function.
- void xuat(char *mssv, char *hoten, char *ntns, char phai, float toan, float ly, float 
hoa);
### Comment.
- Variable naming is difficult and difficult to manage.
- Passing too many parameters to the function.
- Search, sort, copy… difficult.
- Consumes a lot of memory.
### Idea.
- Gather the information of the same student into a new data type => Type struct.
## Declare the structure type.
### Syntax.
```sh
struct <tên kiểu cấu trúc>
{
<kiểu dữ liệu> <tên thành phần 1>;
…
<kiểu dữ liệu> <tên thành phần n>;
};
```
### Example.
```sh
struct DIEM
{
int x;
int y;
};
```
### Explicit syntax.
```sh
struct <tên kiểu cấu trúc>
{
<kiểu dữ liệu> <tên thành phần 1>;
…
<kiểu dữ liệu> <tên thành phần n>;
} <tên biến 1>, <tên biến 2>;
```
### Example.
```sh
struct DIEM
{
int x;
int y;
} diem1, diem2;
```
### The syntax is not explicit.
```sh
struct <tên kiểu cấu trúc>
{
<kiểu dữ liệu> <tên thành phần 1>;
…
<kiểu dữ liệu> <tên thành phần n>;
};
struct <tên kiểu cấu trúc> <tên biến>;
```
### Example.
```sh
struct DIEM
{
int x;
int y;
};
struct DIEM diem1, diem2;// C++ có thể bỏ struct
```
## Use typedef.
### Syntax.
```sh
typedef struct
{
<kiểu dữ liệu> <tên thành phần 1>;
…
<kiểu dữ liệu> <tên thành phần n>;
} <tên kiểu cấu trúc>;
<tên kiểu cấu trúc> <tên biến>;
```
### Example.
```sh
typedef struct
{
int x;
int y;
} DIEM;
DIEM diem1, diem2;
```
## Initialize the struct variable.
### Explicit syntax.
```sh
struct <tên kiểu cấu trúc>
{
<kiểu dữ liệu> <tên thành phần 1>;
…
<kiểu dữ liệu> <tên thành phần n>;
} <tên biến> = {<giá trị 1>,…,<giá trị n>};
```
### Example.
```sh
struct DIEM
{
int x;
int y;
} diem1 = {2912, 1706}, diem2;
```
## Retrieve structured data.
### Characteristics.
- Direct access is not possible.
- Through the structuring element operator. nice also known as dot operator.
**<tên biến cấu trúc>.<tên thành phần>**
### Example.
```sh
struct DIEM
{
int x;
int y;
} diem1;
printf(“x = %d, y = %d”, diem1.x, diem1.y);
```