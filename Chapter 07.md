# Chapter07: BASIC CONCEPTS OF PROGRAMMING
## The basic concepts.
### Computer Programming.
- It is called programming for short.
- The art of putting one or more related abstract algorithms together in a programming language to create a computer program.
### Algorithm.
- A finite set (series) of clearly defined instructions (actions) to solve a particular problem.
## The algorithmic properties.
### Includes the following 5 properties:
- The accuracy.
- The obvious.
- The objectivity.
- The popular.
- The end.
### Steps to build a program.
``` sh
Defining the problem -> Choose solution methods -> Build algorithm/solution -> Install program -> Program editing -> Program implementation.
```
## Example 4
``` sh
#include <stdio.h>
#include<conio.h>

void main()
{
    int Namsinh, Tuoi;
    printf ("Nhập năm sinh của bạn:");
    scanf ("%d", &Namsinh);
    Tuoi = 2022 - Namsinh;
    printf (" Số tuổi của bạn là: %d", Tuoi);
}
```
## Example 5
``` sh
#include <stdio.h>
#include <conio.h>

void main()
{
    int a, b, Tong, Hieu, Tich, Thuong;
    printf("Nhập giá trị a, b:\n");
    scanf("%d%d", &a, &b);
    Tong = a + b;
    Hieu = a - b;
    Tich = a * b;
    Thuong = a / b;
    printf ("Tong của a và b là: %d \n", Tong);
    printf ("Hieu của a và b là: %d\n", Hieu);
    printf ("Tich của a và b là: %d\n", Tich);
    printf ("Thuong của a và b là: %d\n", Thuong);
}
```
## Example 6
``` sh
#include <stdio.h>
#include <conio.h>

void main()
{
    int Tensanpham, Soluong, Dongia, Tien, Tongthanhtoan;
    float VAT;
    printf("Nhập tên sản phẩm:");
    scanf("%s", &Tensanpham);
    printf("Nhập số lượng:\n");
    scanf("%d", &Soluong);
    printf("Nhập đơn giá:\n");
    scanf("%d", &Dongia);
    Tien = Soluong * Dongia;
    VAT = Tien * 0.1;
    Tongthanhtoan = Tien + VAT;
    printf("Tiền cần phải thanh toán: %d\n", Tien);
    printf("Thuế GTGT cần phải trả là: %.0f\n", VAT);
    printf("Tổng tiền cần thanh toán là: %d", Tongthanhtoan);    
}
```