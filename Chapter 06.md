# Chapter 06: PRESENTING INFORMATION IN THE COMPUTER
## Concept.
### Information.
- Concepts used every day.
- Through newspapers, movies, communication...
### Data.
- Representing information using physical signals.
- It makes no sense if they are not organized and handled.
### Information system.
- The system captures data, processes it to create meaningful information or new data.
## Information processing.
- Information processing includes input -> processing -> output (all steps are stored).
## Information measuring unit.
- Binary arithmetic uses two digits 0 and 1.
- Bit ( Binary Digit).
- The smallest unit of information.
- Larger units of information: Byte (B), KiloByte (Kb), MegaByte (MB), GigaByte (GB), TeraByte (TB).
## Information measuring unit.
- 1 bit = 0 => 2^1 = 2.
- 2 bit = 1 0 => 2^2 =4.
- n bit =  n-1 ... 3,2,1,0 => 2^n.
## Decimal.
- Use 10 digits from 0 to 9.
## Binary.
- The numbering system used in electronic computers.
- Use 2 numeric characters 0 and 1.
## Octal.
- Use 8 numeric characters from 0 to 7.
## Hexadecimal.
- Use 16 numeric characters from 0 to 9 and from A to F.
## Converting between numbering systems.
- Humans use decimals.
- Computers use binary, octal, and hexadecimal systems.
- Convert between coefficients.
### Convert from base system b -> DEC.
#### Case one.
- Expand, represent, and compute expressions.
- Example of converting from binary to decimal.
#### Case two.
- Nested Multiply/Divide.
### Convert from DEC -> base system b.
#### Change the integer part.
- Divide the integer part of that number by b and keep taking the integer part of the result divided by b.
- The sequence of remainders at each division is a0 , a1, ..., an.
- The integer part of a base number b is (an...a1a0).
#### Change odd part.
- Multiply the odd part of that number by b and keep multiplying the odd part by b.
- The sequence of integers at each multiplication a-1, a-2, ..., a-m forms an odd part in the base b system.
- Convert 11.25 decimal (rank 10) to binary (b = 2).
``` sh
Change the integer part 11 10
11 : 2 = 5 surplus 1, => a0 = 1
05 : 2 = 2 surplus 1, => a1 = 1
02 : 2 = 1 surplus 0, => a2 = 0
01 : 2 = 0 surplus 1, => a3 = 1
=> Integer part is 11 10 = 10112

Change odd part 0.25 10
• 0.25 * 2 = 0.5, => a-1 = 0
0.50 * 2 = 1.0, => a-2 = 1
=> Odd fractions is 0.25 10 = .01 2
```
### Convert from binary to base system b.
#### From binary to hexadecimal (2^4).
- Group each set of 4 bits in the binary representation and then convert to the corresponding digit in hexadecimal (0000 ~> 0,..., 1111 ~> F).
#### From binary to octal (2^3).
- Group each set of 3 bits in the binary representation and then convert to the corresponding octal digit (000 ~> 0,..., 111 ~> 7).
## Arithmetic operations on the numbering system.
### Summation.
- Adding numbers in other coefficients is done in the same way as in the decimal system.
- In each system should make a table to add numbers and look up in this table for immediate results.
### Subtraction.
- The subtracted numbers are smaller than the subtracted ones, i.e. a - b for a < b.
- To calculate a - b but a > b, we calculate b - a and then invert the result.
### Multiplication.
- Multiplying numbers in other coefficients is done in the same way as in decimal.
### Division.
- Similar to division in decimal system.
## Presenting information in the computer.
- Stored in registers or in memory cells. A register or memory cell is 1 byte (8 bits) or 1 word (16 bits).
- Represents unsigned integers, signed integers, real numbers, and characters.
- msb (most significant bit): heaviest bit (bit n).
- lsb (least significant bit): lightest bit (bit 0).
## Representing unsigned integers.
- Represent values that are always positive.
- All bits are used to represent the value.
- The largest 1-byte unsigned integer is 1111 11112 = 2^8 – 1 = 255 10.
- The largest 1-word unsigned integer is 1111 1111 1111 1111 2 = 2^16 – 1 = 65535 10.
- Depending on your needs, you can use the number 2, 3... word.
Depending on your needs, you can use the number 2, 3... word.
- lsb = 1 then the number is an odd number.
