# Chapter 04: Basis data types.
## Basic data types
### Turbo C has 4 base models as follows:
- Integer type.
- Floating point.
- Type of reasoning.
- Character type.
### Variable
#### Syntax
- <type> <variable name>;
- <type> <variable name 1>, <variable name 2>;
#### For example:
- int i;
- unsigned char dem;
- float ketqua, delta;
### The constant
#### Syntax
- <type> <the constant name> = <value>;
- #define <the constant name> <value> or use const keyword.
#### For example
- int a = 1505;
- int b = 01506;
- int c = 0x1506;
- float d = 15.06e-3;
- #define MAX 100
- const int MAX = 100;
### Expressions 
#### Concept
- Made up of operator and operand.
- Operators acting on the values of the operands
and for a value of a certain type.
- Operator: +, -, *,/.
- Operand: the constant, variable, the function call, etc.
#### For example
- 2 +3, a/5,(a+b)*5,...
### The operator assigns a value to the variable
#### Concept
- Often used on programming.
- Assigns a value to the variable.
#### Syntax
- <variable> = <value>;
- <variable> = <variable>;
- <variable> = <the constant>;
- Variables can be assigned values consecutively.
#### For example
``` sh
void main()
{

int a, b, c, d, e, thuong;
a = 10;
b = a;
thuong = a / b;
a = b = c = d = e = 156;
e = 156;
d = e;
c = d;
b = c;
a = b;

}
```
### The math operators
#### Operator with one operands
- There is only one operand in the expression
- ++ (Increase by 1 unit), -- (decreased by 1 unit)
- Before the operand: perform increment/decrement first.
- After the operand: perform increment/decrement later.
#### for example
- x = 10, y = x ++; // y = 10 and x = 11
- x = 10, y = ++ x; // x = 11 and y = 11
#### Operator with two operands
- There are two operands in the expression.
- +, -, *, /, % (divide by remainder).
- x = x + y <=> x += y;
#### For example
- a = 1 + 2; b = 1 - 2;
- e = 1*1.0/2; f = float(1)/2;
- x = x * (2+3*5); <=> x*= 2 + 3 * 5;
### Operators on bit
#### Operators on bit
- The effects on the bits of the operand.
- & (and), | (or), ^ (xor), ~ (not or get 1's complement).
- >> (shift right), << (shift left).
- Aggregate operator: &=, ^=, ~=, >>=, <<=.
#### For example
``` sh
void main()
{

int a = 5; // 0000 0000 0000 0101
int b = 6; // 0000 0000 0000 0110

int z1, z2, z3, z4, z5, z6;
z1 = a & b; // 0000 0000 0000 0100
z2 = a | b; // 0000 0000 0000 0111
z3 = a ^ b; // 0000 0000 0000 0011
z4 = ~a; // 1111 1111 1111 1010
z5 = a >> 2;// 0000 0000 0000 0001
z6 = a << 2;// 0000 0000 0001 0100

}
```
### Relational operators
#### Relational operators
- Compare two expressions with each other.
- Returns 0 (or false if false) or 1 (or true if true).
- ==, >, <, >=, <, <=, !=.
#### For example
- s1 = (1 == 2).
- s2 = (1 != 2).
- s3 =  (1 > 2).
### Logical operators
#### Logical operators
- Combination of many related expressions.
- && (and), || (or), ! (not).
#### For example
- s1 = (1 > 2) && (3 > 4).
- s2 = (1 > 2) || (3 > 4).
### Conditional operators
#### Conditional operators
- This is a ternary operator (consisting of 3 operands).
- <expression 1> ? <expression 2> : <expression 3> interpreted as <expression 1> is true then the value is <expression 2>. If <expression 1> is false then the value is <expression 3>.
#### For example
- s1 = (1 > 2) ? 2912 : 1706;
- int s2 = 0;
- 1 < 2 ? s2 = 2912 : s2 = 1706;
### Comma operator
#### Comma operator
- Expressions are separated by ,.
- Sub expressions are evaluated from left to right respectively.
- The newly received expression is the value of the rightmost expression.
#### For example
- x = (a++, b = b + 2);
- <=> a++; b = b + 2; x = b;
### The operators precedence
#### Implementation rules
- Execute the expression in the deepest ( ) first.
- Follow the order of precedence of the operators.
- => Automatically add ( ).
#### For example
- n = 2 + 3 * 5; => n = 2 + (3 *5).
### Write expressions for the clauses
- X is greater than or equal to 3: x >= 3.
- a and b have the same sign: (a>0 && b>0) || (a<0 && b<0).
- p equals q equals r: (p == q) && (q == r) or (p == q && q == r).
- –5 < x < 5: (x > –5) && (x < 5) or (x > –5 && x < 5).
### Statements
#### Concept
- A full, direct instruction tells the computer to perform certain tasks.
- The compiler ignores spaces (or tabs or newlines) between statements.
#### For example
``` sh
a=2912;
a = 2912;
a
=
2912;
```
#### Classification
- Single statement: contains only one statement.
- Complex statement (command block): consists of many single statements surrounded by { and }.
#### For example
``` sh
a = 2912; // Single statement.

{     

a = 2912;      // Complex statement.
b = 1706;

}
```
### Output commands
#### Library
- #include <stdio.h> (standard input/output).
#### Syntax
- printf(<format string>[, <đs1>, <đs2>, ...]);
- <format string> is the output information presented and enclosed in double quotes "" inclued: literal text, escape sequence, conversion specifier.
### Format string
#### Literal text
- Outputs exactly as they were typed in the format string.
#### For example
``` sh
String output Hello World
=> printf(“Hello ”); printf(“World”);
=> printf(“Hello World”);
```
#### Escape sequence
- Consists of \ and a character as shown in the following table:
``` sh
\a          Ring tone
\b          Take a step back
\n          Down the line
\t          Tab mark
\\          Imprint \
\?          Imprint ?
\”          Imprint "
```
#### Conversion specifier
- Contains a % sign and a character.
- Specify the type of the variable/value you want to output.
- The main arguments are the output variables/values, listed in comma separated order.
``` sh
%c           Characters             Char
%d, %ld      Signed integer         Ifloat, double
%s           Strings                Char[], char*
%u           Unsigned integer       Unsigned int/short/long
```
### Output Format
#### Syntax
- Integer output format: %nd.
- Real number output format: %n.kd
``` sh
int a = 1706;
float x = 176.85;
printf(“%10d”, a);printf(“\n”);
printf(“%10.2f”, x);printf(“\n”);
printf(“%.2f”, x);printf(“\n”);
```
### String format
#### Combination of ingredients
- int a = 1, b = 2;
- output 1 cong 2 bang 3 and down the line.
``` sh
printf(“%d”, a); // Output the value of the variable a
• printf(“ cong ”); // String output “ cong ”
• printf(“%d”, b); // Output the value of the variable b
• printf(“ bang ”); // String out put “ bang ”
• printf(“%d”, a + b); // Output the value of a + b
• printf(“\n”); // Output control down the line \n
 printf(“%d cong %d bang %d\n”, a, b, a+b);
```
### Input statement
#### Library
- #include <stdio.h> (standard input/output).
#### Syntax
- scanf(<format string>[, <đs1>, <đs1>, ...]);
- <format string> is the same as the output format but only conversion specifier.
- The arguments are the names of the variables that will contain the input value and are preceded by &.
#### For example
- Let a and b be integer types
``` sh
scanf(“%d”, &a); // Enter a value for the variable a
scanf(“%d”, &b); // Enter a value for the variable b
=> scanf(“%d%d”, &a, &b);
```
### Some other useful functions
#### Functions in the math library
- #include <math.h>
- 1 input: double, Result: double
``` sh
 acos, asin, atan, cos, sin, ...
 exp, log, log10
 sqrt
 ceil, floor
 abs, fabs
 ```
 - 2 input: double, Result: double
 ``` sh
 double pow(double x, double y)
 ```
 #### For example
 ``` sh
 int x = 4, y = 3, z = -5;
- float t = -1.2;
- float kq1 = sqrt(x1);
- int kq2 = pow(x, y);
- float kq3 = pow(x, 1/3);
- float kq4 = pow(x, 1.0/3);
- int kq5 = abs(z);
- float kq6 = fabs(t);
```