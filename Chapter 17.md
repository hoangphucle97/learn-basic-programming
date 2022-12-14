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
## The function has default arguments.
- Note: To pass another argument instead of the default one, you must pass the argument in place of the default arguments before it.
- Example: 
```sh
void XuatThongTin(char *hoten, char phai = 0, 
char *lop = “TH07”, int namsinh = 1989)
{
puts(hoten);
printf(phai == 0? “Nam\n” : “Nu\n”);
puts(lop);
printf(“%d”, namsinh);
}
```
- Comment:
    + x = a occurs frequently, then x should be passed as a parameter whose default argument is a. For example, most fade = 0 (male), lop = “TH07” and namsinh = 1989.
    + x = a and y = b happen often but y = b more often should put the default parameter x before y. For example, lop = “TH07” occurs more than fade = 0 so put lop after fade.
## Preprocessor directive #define.
### Symbol constant definition.
- Directive #define <name> <value>.
- Any occurrence of <name> in the source program is replaced by <value> to generate the preprocessor.
- Example:
    + #define MAX 1000
    + #define PI 3.14
    + #define message “Hello World\n”
### Define macros (compound commands - shortcut commands).
- #define <name>(<param-list>) <expression>.
- Any occurrences of <name> with the appropriate number of parameters will be replaced by <expression> (parameters are replaced accordingly).
- Example: 
```sh
- #define showmsg(msg) printf(msg)
- ->showmsg(“Hello”);  printf(“Hello”);
```
## Inline function.
### Example.
```sh
#define PI 3.14159
float addPi(float s)
{
return s + PI;
}
void main()
{
float s = 0;
for (int i = 1; i<=100000; i++)
s = s + PI; // Cách 1 (0.7s)
s = addPi(s); // Cách 2 (1.4s)
}
```
### Comment.
- Using functions makes the program easy to understand but costs the function call.
### Solve.
- Use inline functions by adding the keyword inline before the function's prototype.
-> inline float addPi(float s) { return s + PI;}
### Concept.
- Copy function body to whichever function is called -> same result as method 1.
### Note.
- Reduce function execution time (call and finish).
- Reduce the memory space occupied by subfunctions when the function is called.
- Recursive inline functions are not allowed.
- Most do not allow inline execution of functions using while loops.
- Only inline small functions, inline large functions will be counterproductive (memory for occupied inline function will take longer to release).