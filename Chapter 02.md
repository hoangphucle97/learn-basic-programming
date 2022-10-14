# Chapter 02: Introduction to C language
## Introduce
### The language precursor B
### It is a structured and case sensitive programming language
### Advantages of C language:
- Powerful, flexible.
- Widely used.
- Convertible, little change on different computer systems.
- Easy programming through functions.
### Intergrated development environment:
- EDIT (The source program editor)
- COMPILE (Compiler program)
- RUNTIME (Run the source program)
- DEBUG (Fix source program error)
### Programming environment
- Borland C++ 3.1 for DOS.
- Visual C++ 6.0, Win32 Console Application.
## Vocabulary of the C language
### Characters used
- Alphabet set of 26 Latin characters.
- Decimal digit set.
- Math symbols.
- Special symbols.
- Hyphen and space characters.
### Keyword
- The reserved words in the language
- The keyword cannot be used to name variables, functions, or subroutines.
- Some popular keywords: const, enum, signed, char, double, float, int, case, default, else, if, switch, do, for, while, break, continue, goto, return.
### Indentifier
- A sequence of characters used to indicate the name of a constant, a character constant, the name of a variable, a data type, a function, or a procedure.
- Must not coincide with keywords and be made up of letters and numbers, but the first letter must be a letter or _.
- The maximum number of characters in a name is 255 characters and the character _ can be used in the name, but spaces between spaces are not allowed.
### Indentifier example
- Valid names: Giaiphuongtrinh, Bai_Tap1
- Invalid names: 1A, Giai phuong trinh
- Case sensitive, so the following names are different: A,a; BaiTap, baitap, BAITAP, bAItaP...
### Semicolon
- Used to separate statements.
- For example: printf(“Hello World!”); printf(“\n”);
### Footnotes
- Put between /* */ or // (C++).
- Example: /*Ho & Ten: NVA*/, // MSSV: 0712078.
### Character constants and string constants
- Character constants: 'A', 'a', ...
- String constants: “Hello World!”, “Nguyen Van A”.
- Note: 'A' is different from "A".
### Program structure C
- #include "..." is declare the header file.
- int x; is declare function variables.
- void Nhap(); is function declaration.
- void main() is main function.
- {//} include commands and procedures.
### For example
#include <stdio.h>
#include <conio.h>

void main()
{

int x, y, tong;
printf(“Nhap hai so nguyen: ”);
scanf(“%d%d”, &x, &y);
tong = x + y;
printf(“Tong hai so la %d”, tong);
getch();

}