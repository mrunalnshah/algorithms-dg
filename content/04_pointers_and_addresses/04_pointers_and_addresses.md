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
``` c
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

``` c
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

``` c
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

``` c
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

``` c
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
``` c
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


## Pointer types, void pointers, and pointer arithmetic

**Pointer variables are strongly typed.** It means you need pointer variable of a particular type to store the address of a particular type of variable.  
![[strong-type-req.excalidraw.svg]]  

**Why strong types? Why not some generic types?**  
The answer is that we do not use the pointer variables only to store memory addresses. We also use them to dereference the addresses so that we can access and modify the values in those addresses.

Now as we know that datatypes have different sizes like Integers, Its stored in **4 Bytes**. (integer required 4 bytes, character requires 1 byte and float required 4 bytes)

This variables differ not only in their sizes, they also differ in how we store information in whatever bytes are available for these variables or data types.

Let's say we have an integer:  
![[integer-example-storing.excalidraw.svg]]


> [!NOTE] Pointer Arithmetics
> The only pointer arithmetic that is allowed is **adding** or **subtracting** some constant integer value to/from the pointer variable.

### Void Pointer - Generic Pointer
1. Void pointers are generic pointers, they can store any data types.
2. The caveat is they cannot dereference.

### C Code  
``` c
#include <stdio.h>

int main(){
	int a = 1025;
	int* p;
	
	p = &a;
	  
	printf("size of integer is %lu\n", sizeof(int));
	printf("address = %p, value = %d\n\n",p, *p);
	
	return 0;
}
```

``` c
#include <stdio.h>

int main(){
	int a = 1025;
	int* p;
	
	p = &a;
	  
	printf("size of integer is %lu\n", sizeof(int));
	printf("address = %p, value = %d\n\n",p, *p);
	
	char* pc;
	
	pc = p; // ERROR: CANNOT STORE int* to char*
	
	return 0;
}
```

``` c
#include <stdio.h>

int main(){
	int a = 1025;
	int* p;
	
	p = &a;
	  
	printf("size of integer is %lu\n", sizeof(int));
	printf("address = %p, value = %d\n\n",p, *p);
	  
	char* pc;
	
	pc = (char*) p; // typecasting
	
	printf("size of char is %lu\n", sizeof(char));
	printf("address = %p, value = %d\n\n",pc, *pc); // 1
	
	return 0;
}
```

**Explanation:**  
Why its 1?  
**1025** = 00000000 00000000 00000100 00000001  
char* is 1 byte, so it takes the first byte which is 00000001 and we use %d to print integer so it display's 1.  

``` c
#include <stdio.h>

int main(){
	int a = 1025;
	int* p;  
	
	p = &a;
	
	printf("size of integer is %lu\n", sizeof(int));
	printf("address = %p, value = %d\n",p, *p);
	printf("address = %p, value = %d\n\n",p+1, *(p+1));
	
	char* pc;
	
	pc = (char*) p; // typecasting
	
	printf("size of char is %lu\n", sizeof(char));
	printf("address = %p, value = %d\n",pc, *pc);
	printf("address = %p, value = %d\n\n",pc+1, *(pc+1)); // 4 because 100 in byte 1
	
	return 0;
}
```

``` c
#include <stdio.h>

int main(){
	int a = 1025;
	int* p;
	
	p = &a;
	
	printf("size of integer is %lu\n", sizeof(int));
	printf("address = %p, value = %d\n\n",p, *p);
	  
	// Void Pointer - Generic Pointer
	void* pv;
	  
	pv = p;
	
	printf("Address = %p, value = %d\n", pv, *pv); // ERROR: We cannot dereference void pointer.
	printf("Address = %p\n", pv); // We can only print the address.
	
	return 0;
}
```

``` c
#include <stdio.h>

int main(){
	int a = 1025;
	int* p;
	
	p = &a;
	  
	printf("size of integer is %lu\n", sizeof(int));
	printf("address = %p, value = %d\n\n",p, *p);
	
	// Void Pointer - Generic Pointer
	void* pv;
	  
	pv = p;
	
	printf("Address = %p\n", pv); // We can only print the address.
	printf("Address = %p\n", pv+1); // We can do artihmetic operations on void pointer.
	
	return 0;
}

```

## Pointer to pointer
**Why do we need pointer to integer to reference or store the address of an integer?**  
It's because we don't just store the address of a variable in a pointer variable. We also use the pointer variable to dereference that address and write some value there.

**Can we create a pointer to the variable which is pointer to a variable itself? *We can!***  
![[pointer-to-pointer.excalidraw.svg]]  

### C Code:
``` c
#include <stdio.h>

int main() {
	int x = 5;
	int* p = &x;
	
	*p = 6;
	
	int** q = &p;
	int*** r = &q;
	
	printf("p is %p\n", p); // Address of pointer p
	printf("*p is %d\n\n", *p); // Value at address stored in p // 6
	
	printf("q is %p\n", q); // Address of pointer q
	printf("*q is %p\n", *q); // Value at Address stored in pointer q
	printf("**q is %d\n\n", *(*q)); // Value at address stored in pointer q and value at that address.
	
	printf("r is %p\n", r); // Address of r
	printf("*r is %p\n", *r); // Value of Address stored at pointer r
	printf("**r is %p\n", *(*r)); // Value at address stored in pointer r and value at that address.
	printf("***r is %d\n\n", *(*(*r))); // Value at address stored in pointer r and value at that address and value of that address too.
	
	
	***r = 10;
	printf("***r = 10; x = %d\n\n", x);
	
	**q = *p + 2;
	printf("**q = *p + 2; x = %d\n\n", x);
	
	return 0;
}
```

##  Pointers as a function arguments - call by reference

We have a code:
``` c
// CALL BY VALUE

#include <stdio.h>

void increment(int a){
	a = a + 1;
}

int main(){
	int a;
	
	a = 10;
	
	increment(a);
	
	printf("Value of a = %d", a);
	
	return 0;
}
```  
*Output:*
Value of a = 10  

**Why?**  
To learn this happened, we need to learn first about how memory is allocated in computers for program's to execute.  
![[pointer-as-function-argument.excalidraw.svg]]

So coming back to our program. Why it run like the way it did.  
![[pointer-as-function-arguments-example.excalidraw.svg]]  

> [!NOTE] CRASH OUT
> Stack is fixed size. So if you have a scenario where one function keeps calling another function indefinitely like in the case of indefinite recursion, then the memory of this stack will overflow and our program will crash!

> [!NOTE] Lifetime of Locals
> Lifetime of local variables are till scope of the function executes. Till the function is executing.

So whats happening and how can we fix this ? (Code is perfect, Its the logical error from our side.)  We use **call by value** method. We should use **Call by Reference** as it saves a lot of memory aside from initializing a pointer variable.
![[call-by-value.excalidraw.svg]]

**C Code:**  
``` c
// CALL BY REFERENCE

#include <stdio.h>

void increment(int* a){
	*a = (*a) + 1;
	printf("Address of a in increment: %p\n", &a);
}

  

int main(){
	int a;
	
	a = 10;
	  
	increment(&a);
	
	printf("Address of a in main: %p\n", &a);
	printf("Value of a in main: %d\n", a);
		
	return 0;
}
```

### What is Local vs Global?  
![[local-vs-global.excalidraw.svg]]   

## Pointers and arrays

![[pointers-arrays.excalidraw.svg]]

**Property of Array:** If we just use the name of the Array A, then A gives us the pointer to the first element in the Array.

``` c
int A[5];
int* p;

p = &A[0];
//or
p = A;
```

***Important for Arrays & Pointers in C:***  
**Element at index i**
- Address: `&A[i]` or `(A + i)`
- Value: `A[i]` or `*(A + i)`

**Base Address or Address of first element** is `A` or `&A[0]`

> [!NOTE] Incrementable?
> ```c
> A++; // INVALID
> p++; // VALID
> ```
> Arrays & Pointers are related, not same.
> A has data-type of `int[5]`, while pointer is `int*`. `int[5` decays into a pointer to its first element as `int*`. But decay is temporary.  While address can change, therefore **Increment of p can be done, while increment of A cannot be.**  


**C Code:**  
``` c
#include <stdio.h>

int main() {
	int A[] = {2, 4, 5, 8, 1};  
	
	printf("Address of A is %p\n", A);
	printf("Address of A[0] is %p\n", &A[0]);
	printf("Value of A[0] is %d\n", A[0]);
	printf("Value of A is %d\n\n", *A);
	
	// Loop it
	printf("Loop through Array to find addresses\n");
	for(int i = 0; i < 5; i++){
		printf("Address of A[%d] is %p\n", i, &A[i]);
		printf("Address of A + %d is %p\n",i, A+i);
		printf("Value of A[%d] is %d\n", i, A[i]);
		printf("Value of A + %d is %d\n\n",i, *(A + i));
	}
	
	return 0;
}
```


## Arrays as function arguments



**Work in Progress...**  
Thanks.