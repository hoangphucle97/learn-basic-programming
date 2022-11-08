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