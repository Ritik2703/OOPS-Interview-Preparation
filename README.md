# OOPS-Interview-Preparation
# Hare Krishna
# Radhe Radhe

# Basic Questions
# In Depth 
# Class and Object

-------------------------------------------------------------------------------------------------------------------------------------------------------------
# 1. What is OOPs?

OOPs refer to Object-Oriented Programming system in which programs are treated as a collection of objects. Each object is nothing but an example of a class.

-------------------------------------------------------------------------------------------------------------------------------------------------------------
# 2. Difference between Procedural programming and OOPs?

## Procedural Programming:

It is based on functions.
It reveals the data to the entire program.
It offers less scope of code reuse.
It follows a top-down programming paradigm.
It is complicated in nature, so it is hard to modify, extend and maintain.

## Object-oriented programming:

It is based on real-world objects.
It encapsulates the data.
It provides more scope of code reuse
It follows a bottom-up programming paradigm.
It is less complicated in nature, so it is easier to modify, extend and maintain.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

# 3. What are the basic concepts of OOPs?

The basic concepts of OOPs are:

Inheritance
Encapsulation
Polymorphism
Abstraction
 
----------------------------------------------------------------------------------------------------------------------------------------------------------------
# 4. What is Abstraction?

Abstraction is an OOPs approach to construct the structure of the real-world objects. During the construction, only the general states and behaviours are taken, and more specific states and actions are left aside for the implementers.

# 5. What is Encapsulation?

Encapsulation is an OOPs concept to create and define the restrictions and permissions of an object and its member variable and methods. It is very simple to explain the concept is to make the member variables of a class private and providing public getter and setter methods.

# 6. What is Polymorphism?

Polymorphism is an instance of something in various forms. Java supports multiple forms of polymorphism like polymorphic method, polymorphic reference variable, polymorphic return types and polymorphic argument types.

# 7.  What is inheritance and its types?

A subclass can inherit the behaviours and states of its superclass are known as inheritance. There are various types of inheritance:

Hybrid Inheritance
Multiple Inheritance
Single Inheritance
Multi-level Inheritance
Hierarchical Inheritance

# 8. What is an object, method and class?

Object: An object is an instance of a class. It has its own identity and behaviour.
Class:  Class is a user-defined data type that contains variables, properties and methods.  It determines the properties of an object.
Method:  It is a set of instructions, also called a procedure that is to be performed on the given data.

# 9. What is Static Binding and Dynamic Binding?

Static Binding is a binding in which name can be combined with the class during collection time, and it is also called as early binding.

Dynamic Binding is a binding in which name can be identified with the class during execution time, and it is also known as Late Binding

# 10. What are a constructor and its types?

A constructor is a special kind of method that has the same name as the class and is used to initialize objects of that class. Type of constructor differs from language to language:

Private Constructor
Default Constructor
Copy Constructor
Static Constructor
Parameterized Constructor

# 11. Define overloading and overriding in OOPs?

Overloading is static binding, whereas overriding is productive binding. Overloading is the same method with different arguments, and it may or may not return the equal value in the same class itself.
Overriding is the same method names with the same arguments and return types identified with the class and its child class.

# 12. What are the access modifiers?

Access modifiers define the scope of the method or variable that can be accessed from other various objects.

# 13. What is an abstract class?

An abstract class cannot be proved. Formation of an object is not possible with an abstract class, but it can be inherited. An abstract class can only contain an abstract method, and java allows only abstract method in abstract class while other languages allow non-abstract method as well.

# 14. What are all the operators that cannot be overloaded?

The operators that cannot be overloaded are:

Member Selection
Scope Resolution
Member selection through a pointer to a function

# 15. What does the keyword virtual represented in the method definition?

It represents that we can override the method.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Smallest Class, Creating and deleting its Object.

```
class krishna{             // smallest class
};
int main()
{
   fast
   krishna *k= new krishna;       // create object 
   delete k;                      // delete

   return 0;
}

```
-------------------------------------------------------------------------------------------------------------------------------------------------------

# Exception of Delete - https://www.geeksforgeeks.org/delete-in-c/

## 1. Trying to delete Non-pointer object

```
#include <bits/stdc++.h> 
using namespace std; 
Class Krishna{};
int main() 
{ 
	Krishna x; 
	// Delete operator always 
	// requires pointer as input 
	delete x;
	return 0; 
} 
```

## 2. Trying to delete pointer to a local stack allocated variable.

```
int main() 
{ 
	int x; 
	int* ptr1 = &x; 
	// x is present on stack frame as 
	// local variable, only dynamically 
	// allocated variables can be destroyed 
	// using delete operator 
	delete ptr1; 
	return 0; 
} 
```
----------------------------------------------------------------------------------------------------------------------------------------------------
# new vs malloc() & delete vs free() - https://www.geeksforgeeks.org/new-vs-malloc-and-free-vs-delete-in-c/?ref=rp

We use new and delete operators in C++ to dynamically allocate memory whereas malloc() and free() functions are also used for the same purpose in C and C++. The functionality of the new or malloc() and delete or free() seems to be the same but they differ in various ways.

## malloc() vs new():

#### malloc(): It is a C library function that can also be used in C++, while the “new” operator is specific for C++ only.
#### Both malloc() and new are used to allocate the memory dynamically in heap. But “new” doesn’t call the destructor of a class whereas “malloc()” frees the memory by calling the destructor.

## free() vs delete:

#### free() is a C library function that can also be used in C++, while “delete” is a C++ keyword.
#### free() frees memory but doesn’t call Destructor of a class whereas “delete” frees the memory and also calls the Destructor of the class.

```

// program to illustrate free() and delete keyword in C++ 
#include "bits/stdc++.h" 
using namespace std; 

// Class A 
class A { 
	int a; 

public: 
	int* ptr; 

	// Constructor of class A 
	A() 
	{ 
		cout << "Constructor was Called!"
			<< endl; 
	} 

	// Destructor of class A 
	~A() 
	{ 
		cout << "Destructor was Called!"
			<< endl; 
	} 
 }; 

int main() 
{ 

	// Create an object of class A 
	// using new operator 
	A* a = new A; 
	cout << "Object of class A was "
		<< "created using new operator!"
		<< endl; 

	delete (a); 
	cout << "Object of class A was "
		<< "deleted using delete keyword!"
		<< endl; 

	cout << endl; 

	A* b = (A*)malloc(sizeof(A)); 
	cout << "Object of class A was "
		<< "created using malloc()!"
		<< endl; 

	free(b); 
	cout << "Object of class A was "
		<< "deleted using free()!"
		<< endl; 

	return 0; 
} 
```

# return 0: This statement when executed within the main function calls the destructor of each class for which object was created.
# To avoid the Destructor calling we can replace the statement “return 0” with “exit(0)”.

```
// C++ program to illustrate new, delete 
// malloc() and free() 
#include "bits/stdc++.h" 
using namespace std; 

// Class A 
class A { 
	int a; 

public: 
	int* ptr; 

	// Constructor of class A 
	A() 
	{ 
		cout << "Constructor was Called!"
			<< endl; 
	} 

	// Destructor of class A 
	~A() 
	{ 
		cout << "Destructor was Called!"
			<< endl; 
	} 
}; 

int main() 
{ 

	// Object Created of class A 
	A *a = new A; 
	return 0; 
} 
```
# Output : Constructor was Called

### There is no Destructor call even after using the statement “return 0”. The reason lies in the difference of allocating an object of a class. When we create an object with class_name object_name within a block is created, the object has an automatic storage duration, i.e., it will automatically be destroyed on going out of scope. But when we use new class_name the object has a dynamic storage duration, which means one has to delete it explicitly using delete keyword.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Dynamic Memory Allocation in C using malloc(), calloc(), free() and realloc() - https://www.geeksforgeeks.org/dynamic-memory-allocation-in-c-using-malloc-calloc-free-and-realloc/?ref=rp

defined under <stdlib.h> header file

## malloc()

“malloc” or “memory allocation” method in C is used to dynamically allocate a single large block of memory with the specified size. It returns a pointer of type void which can be cast into a pointer of any form. It initializes each block with default garbage value.

Syntax:
```
ptr = (cast-type*) malloc(byte-size)
For Example:

ptr = (int*) malloc(100 * sizeof(int));
```
Since the size of int is 4 bytes, this statement will allocate 400 bytes of memory. And, the pointer ptr holds the address of the first byte in the allocated memory.

## calloc()

“calloc” or “contiguous allocation” method in C is used to dynamically allocate the specified number of blocks of memory of the specified type. It initializes each block with a default value ‘0’.

Syntax:
```
ptr = (cast-type*)calloc(n, element-size);
For Example:

ptr = (float*) calloc(25, sizeof(float));
```
This statement allocates contiguous space in memory for 25 elements each with the size of the float.

## free
“free” method in C is used to dynamically de-allocate the memory. The memory allocated using functions malloc() and calloc() is not de-allocated on their own. Hence the free() method is used, whenever the dynamic memory allocation takes place. It helps to reduce wastage of memory by freeing it.

Syntax:

free(ptr);

## Realloc
“realloc” or “re-allocation” method in C is used to dynamically change the memory allocation of a previously allocated memory. In other words, if the memory previously allocated with the help of malloc or calloc is insufficient, realloc can be used to dynamically re-allocate memory. re-allocation of memory maintains the already present value and new blocks will be initialized with default garbage value.

Syntax:

ptr = realloc(ptr, newSize);

where ptr is reallocated with new size 'newSize'.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# SMA vs DMA - https://www.geeksforgeeks.org/difference-between-static-and-dynamic-memory-allocation-in-c/?ref=rp

# Memory Allocation: 
Memory allocation is a process by which computer programs and services are assigned with physical or virtual memory space. The memory allocation is done either before or at the time of program execution. There are two types of memory allocations:
1. Compile-time or Static Memory Allocation
2. Run-time or Dynamic Memory Allocation

# Static Memory Allocation: 
Static Memory is allocated for declared variables by the compiler. The address can be found using the address of operator and can be assigned to a pointer. The memory is allocated during compile time.

# Dynamic Memory Allocation:
Memory allocation done at the time of execution(run time) is known as dynamic memory allocation. Functions calloc() and malloc() support allocating dynamic memory. In the Dynamic allocation of memory space is allocated by using these functions when the value is returned by functions and assigned to pointer variables.

<p align="center"><strong><u>Tabular Difference Between Static and Dynamic Memory Allocation in C</u>:</strong></p>
<figure class="table">
<table>
<tbody>
<tr>
<td>
<h3>S.No</h3>
</td>
<td>
<h3>Static Memory Allocation</h3>
</td>
<td>
<h3>Dynamic Memory Allocation</h3>
</td>
</tr>
<tr>
<td>1</td>
<td>In the static memory allocation, variables get allocated permanently.</td>
<td>In the Dynamics memory allocation, variables get allocated only if your program unit gets active.</td>
</tr>
<tr>
<td>2</td>
<td>Static Memory Allocation is done before program execution.</td>
<td>Dynamics Memory Allocation is done during program execution.</td>
</tr>
<tr>
<td>3</td>
<td>It uses <a href="http://www.geeksforgeeks.org/stack-data-structure/">stack</a> for managing the static allocation of memory</td>
<td>It uses <a href="https://www.geeksforgeeks.org/heap-data-structure/">heap</a> for managing the dynamic allocation of memory</td>
</tr>
<tr>
<td>4</td>
<td>It is less efficient</td>
<td>It is more efficient</td>
</tr>
<tr>
<td>5</td>
<td>In Static Memory Allocation, there is no memory re-usability</td>
<td>In Dynamics Memory Allocation, there is memory re-usability and memory can be freed when not required</td>
</tr>
<tr>
<td>6</td>
<td>In static memory allocation, once the memory is allocated, the memory size can not change.</td>
<td>In dynamic memory allocation, when memory is allocated the memory size can be changed.</td>
</tr>
<tr>
<td>7</td>
<td>In this memory allocation scheme, we cannot reuse the unused memory.</td>
<td>This allows reusing the memory. The user can allocate more memory when required. Also, the user can release the memory when the user needs it.</td>
</tr>
<tr>
<td>8</td>
<td>In this memory allocation scheme, execution is faster than dynamic memory allocation.</td>
<td>In this memory allocation scheme, execution is slower than static memory allocation.</td>
</tr>
<tr>
<td>9</td>
<td>In this memory is allocated at compile time.</td>
<td>In this memory is allocated at run time.</td>
</tr>
<tr>
<td>10</td>
<td>In this allocated memory remains from start to end of the program.</td>
<td>In this allocated memory can be released at any time during the program.</td>
</tr>
<tr>
<td>11</td>
<td><strong>Example:</strong> This static memory allocation is generally used for <a href="https://www.geeksforgeeks.org/introduction-to-arrays/">array</a>.</td>
<td><strong>Example:</strong> This dynamic memory allocation is generally used for <a href="http://www.geeksforgeeks.org/data-structures/linked-list/">linked list</a>.</td>
</tr>
</tbody>
</table>
</figure>
<p></p>
