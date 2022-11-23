# Chapter 13: Pointer Data (Advance).
## Level 2 pointer.
- Problem.
```sh
void CapPhat(int *p, int n)
{
p = (int *)malloc(n * sizeof(int));
}
void main()
{
int *a = NULL;
CapPhat(a, 2);
// a vẫn = NULL
}
```
- How to change the value of the pointer (not the value it points to) after calling the function?
### Use an int *&p reference (in C++).
```sh
 void CapPhat(int *&p, int n)
{
p = (int *)malloc(n * sizeof(int));
}
```
### Do not change the parameter that is returned directly
```sh
int* CapPhat(int n)
{
int *p = (int *)malloc(n * sizeof(int));
return p;
}
```
### Use pointer p that points to this pointer a. The function will change the value of pointer a indirectly through pointer p.
```sh
void CapPhat(int **p, int n)
{
*p = (int *)malloc(n * sizeof(int));
}
void main()
{
int *a = NULL;
CapPhat(&a, 4);
}
```
### Note:
```sh
int x = 12;
int *ptr = &x; // OK
int k = &x; ptr = k; // Lỗi

int **ptr_to_ptr = &ptr; // OK
int **ptr_to_ptr = &x; // Lỗi

**ptr_to_ptr = 12; // OK
*ptr_to_ptr = 12; // Lỗi

printf(“%d”, ptr_to_ptr); // Địa chỉ ptr
printf(“%d”, *ptr_to_ptr); // Giá trị ptr
printf(“%d”, **ptr_to_ptr); // Giá trị x
```
## Pointers and two-dimensional arrays.
### Approach 1.
- Elements that make up a 1-dimensional array.
- Use an int * pointer to traverse a 1-dimensional array.
    **int *p = (int *)a**
### Import/Export by one-dimensional array index.
```sh
#define D 3
#define C 4
void main()
{
int a[D][C], i;
int *p = (int *)a;
for (i = 0; i < D*C; i++)
{
printf(“Nhap phan tu thu %d: ”, i);
scanf(“%d”, p + i);
}
for (i = 0; i < D*C; i++)
printf(“%d ”, *(p + i));
}
```
### Relationship between one-dimensional array index and two-dimensional array index.
**(d, c) -> i ?**
**i = d*C + c**

__i -> (d, c) ?__
__d = i / C__
**c = i % C**
### Import/Export by two dimensional array index.
```sh
int a[D][C], i, d, c;
int *p = (int *)a;
for (i = 0; i < D*C; i++)
{
printf(“Nhap a[%d][%d]: ”, i / C, i % C);
scanf(“%d”, p + i);
}
for (d = 0; d < D; d++)
{
for (c = 0; c < C; c++)
printf(“%d ”, *(p + d * C + c));// *p++
printf(“\n”);
}
```
### Approach 2.
- one-dimensional array, each element is a one-dimensional array
    + a contains a[0], a[1]… -> a = & a[0]
    + a[0] contains a[0][0], a[0][1]… -> a[0] = &a[0][0]
### Size of the array.
```sh
void main()
{
int a[3][4];
printf(“KT của a = %d”, sizeof(a));
printf(“KT của a[0] = %d”, sizeof(a[0]));
printf(“KT của a[0][0] = %d”, sizeof(a[0][0]));
}
```
### Comment.
- a is a pointer to a[0], a[0] is a pointer to a[0][0] -> a is a second-level pointer.
- A[0][0] can be accessed in 3 ways.
```sh
void main()
{
int a[3][4];
a[0][0] = 1;
*a[0] = 1;
**a = 1;
a[1][0] = 1; *a[1] = 1; **(a+1) = 1;
a[1][2] = 1; *(a[1]+2) = 1; *(*(a+1)+2) = 1;
}
```
### Pass the array to the function.
- Pass the address of the first element to the function.
- Declare a pointer and then assign the array address to this pointer so that it points to the array.
- This pointer must be of the same type as the array variable, i.e. pointer to n-element memory (array).
- Syntax:
    **<kiểu dữ liệu> (*<tên con trỏ>)[<số phần tử>];**
- Output an array method 1.
```sh
void Xuat_1_Mang_C1(int (*ptr)[4]) // ptr[][4]
{
int *p = (int *)ptr;
for (int i = 0; i < 4; i++)
printf(“%d ”, *p++);
}
void main()
{
int a[3][4]={{1,2,3,4},{5,6,7,8},{9,10,11,12}};
int (*ptr)[4];
ptr = a;
for (int i = 0; i < 3; i++)
Xuat_1_Mang_C1(ptr++); // hoặc ptr + i
Xuat_1_Mang_C1(a++); // sai => a + i
}
```
- Output an array method 2.
```sh
void Xuat_1_Mang_C2(int *ptr, int n) // ptr[]
{
for (int i = 0; i < n; i++)
printf(“%d ”, *ptr++);
}
void main()
{
int a[3][4]={{1,2,3,4},{5,6,7,8},{9,10,11,12}};
int (*ptr)[4];
ptr = a;
for (int i = 0; i < 3; i++)
Xuat_1_Mang_C2((int *)ptr++);
Xuat_1_Mang_C2((int *)(a + i));// a++ sai
}
```
- Output multiple arrays method 1.
```sh
void Xuat_n_Mang_C1(int (*ptr)[4], int n)
{
int *p = (int *)ptr;
for (int i = 0; i < n * 4; i++)
printf(“%d ”, *p++);
}
void main()
{
int a[3][4]={{1,2,3,4},{5,6,7,8},{9,10,11,12}};
int (*ptr)[4];
ptr = a;
Xuat_n_Mang_1(ptr, 3);
Xuat_n_Mang_1(a, 3);
}
```
- Output multiple arrays method 2.
```sh
void Xuat_n_Mang_C2(int (*ptr)[4], int n)
{
int *p;
for (int i = 0; i < n; i++)
{
p = (int *)ptr++;
for (int i = 0; i < 4; i++)
printf(“%d ”, *p++);
printf(“\n”);
}
}
```
## Function pointer.
### Concept.
- Functions are also stored in memory, ie also have addresses.
- Function pointer is a pointer to the memory area containing the function and can call the function through that pointer.
### Explicit declaration.
**<kiểu trả về> (* <tên biến con trỏ>)(ds tham số);**
```sh
// Con trỏ đến hàm nhận đối số int, trả về int
int (*ptof1)(int x);
// Con trỏ đến hàm nhận 2 đối số double, không trả về
void (*ptof2)(double x, double y);
// Con trỏ đến hàm nhận đối số mảng, trả về char
char (*ptof3)(char *p[]);
// Con trỏ đến không nhận đối số và không trả về
void (*ptof4)();
```
### Non-explicit declaration.
**typedef <kiểu trả về> (* <tên kiểu>)(ds tham số);**
**<tên kiểu> <tên biến con trỏ>;**
```sh
int (*pt1)(int, int); // Tường minh
typedef int (*PhepToan)(int, int);
PhepToan pt2, pt3; // Không tường minh
```
