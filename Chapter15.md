# Chapter 16: Strings.
## Concept.
- The char type can only hold one character. To store a string (many characters) we use a (one-dimensional) array of characters.
- String characters end with the character "\0" (null).
- String length = array size – 1.
```sh
char hoten[30]; // Dài 29 ký tự
char ngaysinh[9]; // Dài 8 ký tự
```
## Initialization.
### Initialized like a regular array.
- Specific length.
```sh
char s[10] = {„T‟, „H‟, „C‟, „S‟, „ ‟, „A‟, „\0‟};
char s[10] = “THCS A”; // Tự động thêm „\0‟
```
- Self-determined length.
```sh
char s[] = {„T‟, „H‟, „C‟, „S‟, „ ‟, „A‟, „\0‟};
char s[] = “THCS A”; // Tự động thêm „\0‟
```
## Output string.
- Use the printf function with the “%s” specification.
```sh
char monhoc[50] = “Tin hoc co so A”;
printf(“%s”, monhoc); // Không xuống dòng.
```
- Use the puts function.
```sh
char monhoc[50] = “Tin hoc co so A”;
puts(monhoc); // Tự động xuống dòng
<=> printf(“%s\n”, monhoc);
```
## Input string.
### Use the scanf function with the “%s” specification.
- Only accepts characters from the keyboard until a space or a newline character is encountered.
- The received string does not include whitespace and newline characters.
```sh
char monhoc[50];
printf(“Nhap mot chuoi: ”);
scanf(“%s”, monhoc);
printf(“Chuoi nhan duoc la: %s”, monhoc);
```
### Use the gets function.
- Gets characters from the keyboard until a newline start character is encountered.
- The received string is what the user enters (minus the carriage return).
```sh
char monhoc[50];
printf(“Nhap mot chuoi: ”);
gets(monhoc);
printf(“Chuoi nhan duoc la: %s”, monhoc);
```
## Some functions operate on strings.
### Belongs to the <string.h> library.
- strlen
- strcpy
- strdup
- strlwr/strupr
- strrev
- strcmp/stricmp
- strcat
- strstr
### String length function.
**size_t strlen(const char *s)**
- Calculate the string length s.
- size_t instead of unsigned (in <stddef.h>) used to measure unsigned quantities.
- String length s (excluding terminating characters).
```sh
char s[] = “Visual C++ 6.0”;
int len = strlen(s); // => 14
```