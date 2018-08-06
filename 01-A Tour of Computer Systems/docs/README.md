# A Tour of Computer Systems

## 1.1 Information Is Bits + Context

The source program is a sequence of bits, each with a value of 0 or 1, organized in 8-bit chunks called bytes.


## 1.2 Programs Are Translated by Other Programs into Different Forms

The translation is performed in the sequence of four phases:

1. Preprocessing phase. Read the contents of system header file and insert it directly into the program text.
2. Compilation phase. Translate the text file (modified source program hello.i) into text file hello.s(contain assembly-language program).
3. Assembly phase. Translate hello.s into machine-language instructions, packages them in a relocatable object program.
4. Linking phase. Handling merging separate percompiled objects in a file.

## 1.3 It Pays to Understand How Compilation Systems Work

Reason to understand how compilation systems work:
1. Optimizing program performance.
2. Understanding link-time errors.
3. Avoiding security holes.
