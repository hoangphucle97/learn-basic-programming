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

