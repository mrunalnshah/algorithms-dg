---
title: "Chapter 2: Pointers & Addresses"
draft: false
tags:
  - Chapter
date: 2026-02-02
---

> [!NOTE] Highly Recommended
> Kindly watch (Notes are prepared using this): https://www.youtube.com/watch?v=zuegQmMdy8M 

***Note: This chapter is purely `C` and `C++`  programming oriented.***  

## Basics of Pointers

**Pointers** are variables that store address of another variable.   

For example: This is an empty computer memory like we talked about RAM in previous chapter [[02_ram_and_bits| RAM and Bits]] . To summarize: to store an **int** we need 4 bytes of space, to store a character, we need 1 byte of memory and to store a float, we need 4 bytes of memory or space.  
![[Computer-memory-empty.excalidraw.svg]]  

If  we store, int a & char c in RAM:  
![[computer-memory-full.excalidraw.svg]]  

**How do function like a++ works?**  
- System looksup `a` in RAM.
- Goes to the looked up address, in this case `204`
- adds `1`. (this is not simple, in C adding 1 means adding `sizeof(int) * 1` to the current address which is `204`. So it becomes `208`.)

To reiterate:  
**Pointers are variables that store address of another variable.**

Here, we store a = 4, and b = 10 to memory. We than define a pointer p which stores the address of a. 

![[computer-memory-pointer.excalidraw.svg]]  

**C Code**  
``` C
#include <stdio.h>

int main(){
	int a; // integer 'a'
	int* p; // integer pointer 'p'.
	
	printf("Address of a is %p\n", &a);
	printf("Value of p is %p\n", p);
	  
	return 0;
}
```

Output:
![[Output_1.excalidraw.svg]]  

## Working with pointers
**Again, Pointers are variables that store address of other variables.**  


> [!NOTE] type for a type
> We need same datatype to the pointer variable that of the variable to store an address of the variable.
> ![[same-type-pointers.excalidraw.svg]]  
> 


### Working with Codes

``` C
#include <stdio.h>

int main(){
	int a;
	int* p;
	
	p = &a;
	
	printf("%p\n", p);
	printf("%d\n", *p);
	  
	return 0;
}
```

``` C
#include <stdio.h>

int main(){
	int a;
	int* p;
	
	p = &a;
	a = 10;
	  
	printf("Address stored at p: %p\n", p);
	printf("Value stored at address of p: %d\n", *p);
	
	printf("Address of a: %p\n", &a);
	printf("Address of p: %p\n", &p);
	
	return 0;
}
```

``` C
#include <stdio.h>

int main(){
	int a;
	int* p;
	
	p = &a;
	a = 10;
	  
	printf("a = %d\n", a);
	
	*p = 12; // dereferencing
	
	printf("a = %d\n", a);
	
	return 0;
}
```

``` C
#include <stdio.h>

int main() {
	int a;
	int* p;
	
	a = 10;
	p = &a;
	
	printf("Address of p is %p\n", p);
	printf("Value at Address stored at p is %d\n\n", *p);
	
	int b = 20;
	*p = b;
	
	printf("Address of p is %p\n", p);
	printf("Value at Address stored at p is %d\n\n", *p);
	
	p = &b;
	
	printf("Address of p is %p\n", p);
	printf("Value at Address stored at p is %d\n", *p);
	
	return 0;
}
```

**Pointer Arithmetic - We add 1 to the current address to get what? Next Address, or next integer?**
``` C
#include <stdio.h>

int main(){
	int a = 10;
	int* p;
	
	p = &a;
	
	// Pointer Arithmetic
	printf("Address of p is %p\n",p); // p is 2002
	printf("Value at address p is %d\n\n",*p);
	
	printf("Size of integer is %lu bytes\n\n", sizeof(int));  
	
	printf("Address of p + 1 is %p\n",p+1); // p is 2006, why ? p + 1 moves to next integer so its +4 (size of int)
	printf("Value at address p+1 is %d\n\n",*(p+1));
	
	printf("Address of p + 2 is %p\n",p+2); // p + 8 --> 2 integers moved ahead.
	printf("Value at address p+2 is %d\n\n",*(p+2));
	
	return 0;
}
```


**Work in Progress...**  
Thanks.