# Chapter 17: ADVANCED FUNCTION (Part 1).
## The parameters of the main function.
### The parameters of the main function.
```sh
void main(int argc, char *argv[])
{
…
}
```
- In there:
    + argc is the number of arguments (including program file names).
    + argv is an array of arguments (in the form of strings).
- Example: Write a program named Cong that takes 2 arguments x and y and outputs the value x + y.
```sh
#include <stdio.h>
#include <stdlib.h> // atoi
void main(int argc, char *argv[]) {
if (argc == 3) {
int x = atoi(argv[1]);
int y = atoi(argv[2]);
printf(“%d + %d = %d”, x, y, x+y);
}
else
printf(“Sai! VD: Cong 2912 1706”);
```
- Example: Write a program named test that receives data from the input.txt file, processes it, and outputs the results to the output.txt file.
```sh
#include <stdio.h>
void main(int argc, char *argv[]) {
if (argc == 3) {
// Nhập dữ liệu từ tập tin argv[1]
// Xử lý
// Xuất kết quả ra tập tin argv[2]
}
else
printf(“Sai! VD: test in.txt out.txt”);
}
```
- Example: Write a Tong function to calculate the sum of 4 numbers x, y, z, t.
```sh
int Tong(int x, int y, int z, int t)
{
return x + y + z + t;
}
```