---
title: "Chapter 1: RAM and Bits"
draft: false
tags:
  - Chapter
  - RAM
  - Bits
date: 2026-01-13
---

> [!NOTE] Grogu or Yoda? 
> ***Day one: Grogu smashing buttons. 
> Day one thousand: Yoda explaining why the button matters.***
## What is a RAM?
![[8gb-ram-crucial-ddr4.webp]]

***Figure 1: Crucial 8GB 2400MHz DDR4 SODIMM Laptop Memory***

RAM (for Random Access Memory) is used to store `runtime data` in the form of `data structure`.  Figure 1 shows the image of how a RAM looks like. Runtime data is the data required to run the computers. Your image is a storage-data, but when you double click on the data, it loads the storage-data into runtime memory in RAM which becomes runtime data.

### **So what is a Data Structure?**
In simple words, Its structuring of data in temporary storage (e.g. RAM - Runtime Storage) or permanent storage (e.g. Solid State Drive) to access it with ease.  For example, when you want to store an `integer` in your storage you can't allocate the space required for a `character`, or `float` or `image` to be stored and vice versa. You require a specific amount of `bits` and specific amount of `structuring of those bits` to get your `integer` stored in your computer for further use.  

Examples of Data Structures:

| Data Structure   | Values Stored                       |
| ---------------- | ----------------------------------- |
| integer (int)    | ..., -3, -2, -1, 0, 1, 2, 3, ...    |
| float            | -3.14, -1.0, 0.5, 1.5, 100.984      |
| character (char) | a, A, b, c, ..., $, #, ₹, (, ), ... |
| Gender           | Male, Female                        |

- ***Integer, Float, Character are `primitive` data structures meaning they built-in by developers of the language for us.***
- ***Gender, on the other hand, is a `User-Defined` data structure which is built by us for storing a gender related data for a ease of use.***

> [!NOTE] Size of a typical RAM?
> It is very common for RAM to come in 4 GB, 8 GB, 12 GB, 16 GB, 32 GB, 64 GB, ...
### So what is GB in 8 GB?
![[8-bit-draw.excalidraw.svg| 800x500]]
**`8 GB` is approximately a `8,589,934,592 bytes`, which is `68,719,476,736 bits` and each bit stores either `0` or `1`.**

### Reality of 0's and 1's?
- A bit is either `0` or `1` is an abstract form. Under the hood, its `transistors` that scores data in the form of `voltage`.
- In Reality:
	- `0` means low voltage.
	- `1` means high voltage.
- Computer works with low and high voltages. (there is a constant flow of voltage in transistors).
###  Storing an Integer {1, 7} in Computers:
**Note:** Integers use 4 bytes which is 4 x 8 = 32 bits 

#### Storing 1
![[32-bit-integer-1.excalidraw.svg| 800x100]]
#### Storing 7
![[32-bit-integer-7.excalidraw.svg| 800x100]]

### What is happening?

![[2n-annotation.excalidraw.png| 800]]
#### Bits are stored in group of 8 bits.
- bits are in the form of  $2^n$
- Power of 2's with maximum value can be:  $2^0, 2^1, 2^2, 2^3, 2^4, ... = 1, 2, 4, 8, 16, ...$
- For Example:
	- 1: $2^0$ x 1 + (rest 31 bits are 0) = 1.
	- 7: $2^0$ x 1 + $2^1$ x 1 + $2^2$ x 1 + (rest 29 bits are 0) = 7
## What is Array?
Array is a contiguous block of data in a storage. 
### How arrays are stored in RAM?

**Note:** one of the RAMs functionality is to allocate space for our work. RAM can allocate memory or space randomly anywhere within it.  

- Most Integers are stored in `bytes of 4`. Therefore, when parsing an array of integer, we add `+4` in to get another integer in the array. 
![[how-arrays-are-stored-integer.excalidraw.svg|800]]
- Most ASCII characters are stored in `1 byte`. Therefore, when parsing an ASCII character in array, we add `+1` after first character to get another character.
![[how-arrays-are-stored-character.excalidraw.svg| 800]]
***Maybe, It can be overwhelming at first, but its very simple.***
## Bit Logical" Operations
- **Manipulating the bits**
- Bits are either `0` or `1`. 
- Just like logic like:
	- Cake `or` Sandwich
	- Games `and` Study
	- `not` happy
- We can use the same logic for our bits.
- ***1 is `True`, 0 is `False`.***
### AND
- denoted with `&` in many programming languages.
- N = 1 & 1 = 1

| IN 1 | Operation | IN 2 | OUT |
| ---- | --------- | ---- | --- |
| 0    | &         | 0    | 0   |
| 0    | &         | 1    | 0   |
| 1    | &         | 0    | 0   |
| 1    | &         | 1    | 1   |
### OR
- denoted with `|` in many programming languages.
- N = 1 | 0 = 1

| IN 1 | Operation | IN 2 | OUT |
| ---- | --------- | ---- | --- |
| 0    | \|        | 0    | 0   |
| 0    | \|        | 1    | 1   |
| 1    | \|        | 0    | 1   |
| 1    | \|        | 1    | 1   |

### XOR
- denoted with `^` in many programming languages.
- N = 0 ^ 1 = 1 

| IN 1 | Operation | IN 2 | OUT |
| ---- | --------- | ---- | --- |
| 0    | ^         | 0    | 0   |
| 0    | ^         | 1    | 1   |
| 1    | ^         | 0    | 1   |
| 1    | ^         | 1    | 0   |
### NOT (also called `negation`)
- denoted with `~` in many programming languages. Sometimes `!` is also used to represent negation.
- N = ~1 = 0

| IN  | Operation | OUT |
| --- | --------- | --- |
| 0   | ~         | 1   |
| 1   | ~         | 0   |
## Bit Shifting Operation
- Computer widely uses bit shifting for:
	- Performance Optimizations like multiplication/division by powers of two into shifts for speed.
	- Low-level programming of computers which directly manipulates bits give better performance.
- Two bit shifting operations:
	- `>>` (Right shift): Shift the bit to the right, add 0 from the left.
	- `<<` (Left shift): Shift the bit to the left, add 0 from the right.
- Example: N  = 11 `(1011)`

| Operations | Method    | Output |
| ---------- | --------- | ------ |
| Load       | 1011      | 1011   |
| >>         | 1011 >> 1 | 0101   |
| <<         | 0101 << 1 | 1010   |
| >>         | 1010 >> 1 | 0101   |
| >>         | 0101 >> 1 | 0010   |
| >>         | 0010 >> 1 | 0001   |
| >>         | 0001 >> 1 | 0000   |

**This is bit shifting, again it can be overwhelming, but its not.**

**This is all about RAM and Bits. You can read more about how a computer works under the hood in your free time with below resources:** 
# Supplementary Resources
1. [NAND2TETRIS](https://www.nand2tetris.org/)
2. [Build your own 8-bit computer from scratch](https://eater.net/8bit) by Ben Eater
## Next?
- You can go back to: [[01_introduction| Introduction]]
- or You can move forward to next chapter: [[03_abstraction | Concept 1: Abstraction]]