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
### String copy function.
**char *strcpy(char *dest, const char *src)**
- Copies the string src to the string dest, stopping when the terminating character '\0' has just been copied.! dest must be large enough to accommodate src.
```sh
char s[100];
s = “Visual C++ 6.0”; // sai
strcpy(s, “Visual C++ 6.0”); // đúng
```
### Copy constructor.
**char *strdup(const char *s)**
- Make a copy of a given string s. The function will automatically create a long memory area strlen(s) + 1 (bytes) to hold the string s. This memory area must be destroyed automatically when not in use.
```sh
char *s;
s = strdup(“Visual C++ 6.0”);
```
### The function converts to a regular string.
**char *strlwr(char *s)**
- Convert string s to normal string ('A' to 'a', 'B' to 'b', …, 'Z' to 'z').
```sh
char s[] = “Visual C++ 6.0”;
strlwr(s);
puts(s); // visual c++ 6.0
```
### Function converts to string IN.
**char *strupr(char *s)**
- Convert strings to string IN ('a' to 'A', 'b' to 'B', …, 'z' to 'Z').
```sh
char s[] = “Visual C++ 6.0”;
strupr(s);
puts(s); // VISUAL C++ 6.0
```
### String reverse function.
**char *strrev(char *s)**
- Reverse the order of characters in the string s (except the terminating character).
```sh
char s[] = “Visual C++ 6.0”;
strrev(s);
puts(s); // 0.6 ++C lausiV
```
### The function compares two strings.
**int strcmp(const char *s1, const char *s2)**
- Compares two strings s1 and s2 (case sensitive).
```sh
char s1[] =
“visual C++ 6.0”;
char s2[] =
“Visual C++ 6.0”;
int kq = strcmp(s1, s2); // => kq > 0
```
**int stricmp(const char *s1, const char *s2)**
- Compares two strings s1 and s2 (case insensitive).
```sh
char s1[] =
“visual c++ 6.0”;
char s2[] = “VISUAL C++ 6.0”;
int kq = stricmp(s1, s2);// => kq == 0
```
### Function to concatenate two strings.
**char* strcat(char *dest, const char *src)**
- Append the src string after the dest string. ! The dest string must be sufficient to contain the result.
```sh
char s1[100] = “Visual C++”;
char s2[] =
“6.0”;
strcat(s1,
“ ”); // => “Visual C++ ”
strcat(s1, s2); // => “Visual C++ 6.0”
```
### Function to find a string within a string.
**char* strstr(const char *s1, const char *s2)**
- Find the position of the first occurrence of s2 in s1.
```sh
char s1[] = “Visual C++ 6.0”;
char s2[] = “C++”;
if (strstr(s1, s2) != null)
printf(“Tim thay s2 trong s1…”);
```