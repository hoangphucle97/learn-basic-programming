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
## Assign structured data.
### Have two way.
- <biến cấu trúc đích> = <biến cấu trúc nguồn>;
- <biến cấu trúc đích>.<tên thành phần> = <giá trị>;
### Example.
```sh
struct DIEM
{
int x, y;
} diem1 = {2912, 1706}, diem2;
…
diem2 = diem1;
diem2.x = diem1.x;
diem2.y = diem1.y * 2;
```
## Complex structure.
### The composition of a structure is another structure.
```sh
struct DIEM
{
int x;
int y;
};
struct HINHCHUNHAT
{
struct DIEM traitren;
struct DIEM phaiduoi;
} hcn1;
…
hcn1.traitren.x = 2912;
hcn1.traitren.y = 1706;
```
### The members of the structure are arrays.
```sh
struct SINHVIEN
{
char hoten[30];
float toan, ly, hoa;
} sv1;
…
strcpy(sv1.hoten, “Nguyen Van A”);
sv1.toan = 10;
sv1.ly = 6.5;
sv1.hoa = 9;
```
### Recursive (self-pointing) structure.
```sh
struct PERSON
{
char hoten[30];
struct PERSON *father, *mother;
};
struct NODE
{
int value;
struct NODE *pNext;
};
```
### The composition of the struct is sized in bits.
```sh
struct bit_fields
{
int bit_0 : 1;
int bit_1_to_4 : 4;
int bit_5 : 1;
int bit_6_to_15 : 10;
};
```
## The size of the struct.
### Example.
```sh
struct A
{
int a;
double b;
};
sizeof(A) = ???
```
```sh
struct B1
{
int a;
int b;
double c;
};
sizeof(B1) = ???
```
```sh
struct B2
{
int a;
double c;
int b;
};
sizeof(B2) = ???
```
## Directive #pragma pack.
### Directive #pragma pack (n).
-  n = 1, 2, 4, 8, 16 (byte)
- The maximum boundary of the elements in the struct.
    + BC n default is 1
    + VC++ n default is 8
    + Project settings -> Compile Option C/C++ -> Code Generation -> Structure Alignment
- Boundary for 1 structure.
```sh
#pragma pack(push, 1)
struct MYSTRUCT { … };
#pragma pack(pop)
```
## #pragma pack
### Example (without #pragma pack (1).)
```sh
struct A {
double a;
int b;
int c;
};
struct B {
int b;
double a;
int c;
};
struct C {
int b;
int c;
double a;
};
```
### Structure notes.
- The struct type is defined to be the format and the struct variable is declared to use the defined format.
- In C++, struct keyword can be omitted when declaring variables (or using typedef).
- When entering real numeric variables in the structure, it must be entered through an intermediate variable.
```sh
struct DIEM { float x, y;} d1;
float temp; scanf(“%f”, &temp); d1.x = temp;
```