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
