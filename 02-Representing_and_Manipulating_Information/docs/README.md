# Representing and Manipulating Information

Modern computers store and process information represented as 2-valued signals.

We consider the three most important representations of numbers:
1. Unsigned encodings are based on traditional binary notation, representing numbers greater than or equal to 0.
2. Two’s-complement encodings are the most common way to represent signed integers, that is, numbers that may be either positive or negative.
3. Floating-point encodings are a base-two version of scientiﬁc notation for representing real numbers.

Computer representations use a limited number of bits to encode a number, and hence some operations can overﬂow when the results are too large to be represented.


The different mathematical properties of integer vs. ﬂoating-point arithmetic stem from the difference in how they handle the ﬁniteness of their representations—integer representations can encode a comparatively small range of values, but do so precisely, while ﬂoating-point representations can encode a wide range of values, but only approximately.

We can understand the ranges of values that can be represented and the properties of the different arithmetic operations. This understanding is critical to writing programs that work correctly over the full range of numeric values and that are portable across different combinations of machine, operating system, and compiler.

## 2.1 