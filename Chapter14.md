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
## Dynamic memory allocation.
### void *malloc(size_t size).
- Allocate in HEAP a memory area size
(bytes) size_t instead of unsigned (in <stddef.h>).
### void *calloc(size_t num, size_t size).
- Allocate memory including **num** elements in HEAP, each element **size** (bytes).
### void *realloc(void *block, size_t size).
- Allocate a memory area of size size because the block points to it in HEAP memory.
    + block == NULL -> use malloc.
    + size == 0 -> use free.
### void free(void *ptr).
- Frees the memory pointed to by ptr, which is allocated by the functions malloc(), calloc(), realloc(). If ptr is NULL then do nothing.
### <pointer_to_datatype> = new <datatype>[size].
- Allocate a memory area of size
sizeof(<datatype>)*size in HEAP.
### delete []<pointer_to_datatype>.
- Frees the memory in HEAP pointed to by <pointer_to_datatype> (allocated with new).
### Note.
- No need to check the pointer for NULL before free or delete.
- Allocating with malloc, calloc or realloc is freed, allocating with new is freed by delete.
- Allocating with new is freed with delete, allocating an array with new [] is freed with delete [].
## Operations on memory blocks.
### void *memcpy(void *dest, void *src, size_t count).
- Copy exact count bytes from block src to block dest.
- If two memory blocks overlap, the function will not work correctly.
### void *memmove(void *dest, void *src, size_t count).
- Copy exact count bytes from block src to block dest.
- If two memory blocks overlap, the function still executes correctly.
### void *memset(void *dest, int c, size_t count).
- Set the first count (bytes) of the memory area that dest points to equal the value c (from 0 to 255).
- Usually used for char type memory, and other type memory is usually set to zero.