# Representing and Manipulating Information

Modern computers store and process information represented as 2-valued signals.

We consider the three most important representations of numbers:
1. Unsigned encodings are based on traditional binary notation, representing numbers greater than or equal to 0.
2. Two’s-complement encodings are the most common way to represent signed integers, that is, numbers that may be either positive or negative.
3. Floating-point encodings are a base-two version of scientiﬁc notation for representing real numbers.

Computer representations use a limited number of bits to encode a number, and hence some operations can overﬂow when the results are too large to be represented.


The different mathematical properties of integer vs. ﬂoating-point arithmetic stem from the difference in how they handle the ﬁniteness of their representations—integer representations can encode a comparatively small range of values, but do so precisely, while ﬂoating-point representations can encode a wide range of values, but only approximately.

We can understand the ranges of values that can be represented and the properties of the different arithmetic operations. This understanding is critical to writing programs that work correctly over the full range of numeric values and that are portable across different combinations of machine, operating system, and compiler.

## 2.1 Information Storage

Most computers use blocks of eight bits, or byte as the smallest addressable unit of memory.

Every byte of memory is identiﬁed by a unique number, known as its address, and the set of all possible addresses is known as the virtual address space.

Various mechanisms are used to allocate and manage the storage for different parts of the program. This management is all performed within the virtual address space.
### 2.1.1 Hexadecimal Notation

A single byte consists of 8 bits. Its value range from 0B00000000 to 0B11111111. viewing as decimal integer, its value range from 0 to 255.

Hexadecimal use digits '0' through '9' along with characters 'A' through 'F' to represent 16 possible values. Numeric constants start with 0x or 0X are interpreted as being in hexadecimal. character may be written in either upper or lower case.