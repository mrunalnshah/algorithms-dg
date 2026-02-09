---
title: "Chapter 3: Arrays"
draft: false
tags:
  - Chapter
date: 2026-01-30
---
## Arrays
Continuous block of allocated space or memory in RAM.  
![[array-diagram.excalidraw.svg]]    

**Arrays can be:**
1. Static - Fixed Size Memory
2. Dynamic - Fixed Size Allocated but can be reallocated to a bigger fixed size. 

### Static Arrays
- They are fixed size arrays. Once allocated they cannot hold more values than original size.  
- Therefore, Static Arrays cannot:
	- Increase Size
	- Store anywhere else  
![[static-array-2.excalidraw.svg]]  
- **Properties of Static Arrays:**
	- Read
		- Read at Index - **O(1)**
	- Write (Insert)
		- Insert at Start - **O(n)**
		- Insert at End - **O(1)**
		- Insert anywhere Middle - **O(n)**
		- Insert Anywhere - **O(n)**
	- Write (Remove)
		- Remove at Start - **O(n)**
		- Remove at End - **O(1)**
		- Remove anywhere Middle - **O(n)**
		- Remove from anywhere - **O(n)**

> [!NOTE] Programming Languages and Arrays
> Some languages like Python, JavaScript uses only dynamic arrays, while some languages like C, C++ provides Static and dynamic array.
### Operations
#### Read
Reading an element in the array is **O(1)** time complexity. Because of RAM, which literally means Random Access Memory, we can read at any location of the array given we have its index.

#### Write (Insert)
Writing an element in the array as worst case can be **O(n)**, while in the best case, it can be **O(1)**. 
- Inserting or Removing at end is **O(1)**.
- Inserting or Removing at start is **O(n)**
- Inserting or Removing anywhere in middle is **O(n)**.

### Code Implementation
#### Python  
**Implementing Static Array in Python is a joke. You can force yourself, but I would suggest to use C to implement this.**
#### C  
``` c
```
#### Rust  
``` rust
```

## Dynamic Array