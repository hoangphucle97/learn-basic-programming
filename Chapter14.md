# DATA TYPE CONVERT AND DYNAMIC MEMORY SUPPLY.
## The need for type conversion.
### Every data object in C has a defined type.
- Variables of type char, int, float, double, ...
- Pointers to char, int, float, double, ...
### How to deal with an expression with different types?
- C automatically converts the type (type compression).
- The user can change the type by himself.
## Automatic style conversion.
### Escalation (data type) in the expression.
- Components of the same type
    + The result is a generic type
    + int / int -> int, float / float -> float
    + Example: 2 / 4 -> 0, 2.0 / 4.0 -> 0.5
- Other types of components
    + The result is the most comprehensive type
    + char < int < long < float < double
    + float / int -> float / float, …
    + Example: 2.0 / 4 -> 2.0 / 4.0 -> 0.5
- Note, only temporary (internal) conversions.
### Phép gán <BT trái> = <BT phải>;.
- The BT on the right side is always leveled up (or downgraded) temporarily to resemble the BT on the left side.
```sh
int i;
float f = 1.23;
```
- Possible loss of integer precision when converting to real numbers -> restriction!
```sh
int i = 3;
float f;
f = i; // -> f = 2.999995
```
### Explicit conversion (type coercion).
- Actively convert (temporary) type to avoid erroneous results.
**(<kiểu chuyển đổi>)<biểu thức>;**
```sh
int x1 = 1, x2 = 2;
float f1 = x1 / x2; // -> f1 = 0.0
float f2 = (float)x1 / x2; // -> f2 = 0.5
float f3 = (float)(x1 / x2); // -> f3 = 0.0
```
## Static and dynamic memory allocation.
### Static memory allocation.
- Declare variables, structures, arrays, ...
- It is imperative to know in advance how much storage memory is needed -> consumes memory, cannot be resized, ...
### Dynamic memory allocation.
- Available upon request.
- Can be released if not needed.
- Using memory outside the program (including virtual memory).