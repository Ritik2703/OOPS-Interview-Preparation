# OOPS-Interview-Preparation
# Hare Krishna
# Radhe Radhe

# https://wiki.sei.cmu.edu/confluence/display/cplusplus/

# Basic Questions
# In Depth 
# Class and Object
# SMA vs DMA
# Constructor & destructor
# Encapsulation
# Access Modifier
# Polymorphism
# Inheritance
# 


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
# 3. What is an object, method and class?

Object: An object is an instance of a class. It has its own identity and behaviour.
Class:  Class is a user-defined data type that contains variables, properties and methods.  It determines the properties of an object.
Method:  It is a set of instructions, also called a procedure that is to be performed on the given data.

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

# return 0: 
#### This statement when executed within the main function calls the destructor of each class for which object was created.
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

<p align="center"><strong><u>Tabular Difference Between Static and Dynamic Memory Allocation</u>:</strong></p>
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

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 4. What are a constructor and its types?

A constructor is a special kind of method that has the same name as the class and is used to initialize objects of that class. Type of constructor differs from language to language:

Private Constructor
Default Constructor
Copy Constructor
Static Constructor
Parameterized Constructor

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Constructor - https://www.geeksforgeeks.org/constructors-c/

A constructor is a member function of a class which initializes objects of a class. In C++, Constructor is automatically called when object(instance of class) create. It is special member function of the class.

## How constructors are different from a normal member function?

A constructor is different from normal functions in following ways:
1. Constructor has same name as the class itself
2. Constructors don’t have return type
3. A constructor is automatically called when an object is created.( Default and Copy Constructor)
4. If we do not specify a constructor, C++ compiler generates a default constructor for us (expects no parameters and has an empty body).

## Types of Constructor-

1. Default Constructor
2. Parametrized Constructor
3. Copy Constructor - The compiler created copy constructor works fine in general. We need to define our own copy constructor only if an object has pointers or any runtime allocation of the resource like file handle, a network connection..etc.

# When is copy constructor called?

In C++, a Copy Constructor may be called in following cases:
1. When an object of the class is returned by value.
2. When an object of the class is passed (to a function) by value as an argument.
3. When an object is constructed based on another object of the same class.
4. When the compiler generates a temporary object.

# Shallow Copy vs Deep Copy-
 Default constructor does only shallow copy.
 ![shallow](https://media.geeksforgeeks.org/wp-content/uploads/copy-constructor.png)

Deep copy is possible only with user defined copy constructor. In user defined copy constructor, we make sure that pointers (or references) of copied object point to new memory locations.
 ![Deep](https://media.geeksforgeeks.org/wp-content/uploads/copy-constructor1.png) 

# Copy constructor vs Assignment Operator
Which of the following two statements call copy constructor and which one calls assignment operator?
```
MyClass t1, t2; 
MyClass t3 = t1;  // ----> (1) 
t2 = t1;          // -----> (2)  
```

Copy constructor is called when a new object is created from an existing object, as a copy of the existing object. Assignment operator is called when an already initialized object is assigned a new value from another existing object. In the above example (1) calls copy constructor and (2) calls assignment operator. 

See this for more details.
```
 class krishna{
   public:
   krishna()
   {
   cout<<"Default Constructor";
   }
   Krishna(int k)
   {
   cout<<"Parametrized Constructor";
   }
   krishna( krishna &k)
   {
   cout<<"Copy Constructor";
   }
   krishna operator = (krishna &k)
   {
   cout<<"assignment operator";
   }
  };
  int main()
  {
    Krishna k;
    krishna k2(6);
    krishna k3=k,k4;
    k4=k;
    return 0;
   }
 ```
# Can we make copy constructor private?
Yes, a copy constructor can be made private. When we make a copy constructor private in a class, objects of that class become non-copyable. This is particularly useful when our class has pointers or dynamically allocated resources. In such situations, we can either write our own copy constructor like above String example or make a private copy constructor so that users get compiler errors rather than surprises at runtime.

# Why argument to a copy constructor must be passed as a reference?
A copy constructor is called when an object is passed by value. Copy constructor itself is a function. So if we pass an argument by value in a copy constructor, a call to copy constructor would be made to call copy constructor which becomes a non-terminating chain of calls. Therefore compiler doesn’t allow parameters to be passed by value.

# Why argument to a copy constructor should be const?
so that objects are not accidentally modified

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Deconstructor - https://www.geeksforgeeks.org/destructors-c/
Destructor is a member function which destructs or deletes an object.

## When is destructor called?
A destructor function is called automatically when the object goes out of scope:
(1) the function ends
(2) the program ends
(3) a block containing local variables ends
(4) a delete operator is called 
## How destructors are different from a normal member function?
Destructors have same name as the class preceded by a tilde (~)
Destructors don’t take any argument and don’t return anything
 
# Can there be more than one destructor in a class?
No, there can only one destructor in a class with classname preceded by ~, no parameters and no return type.

# When do we need to write a user-defined destructor?
If we do not write our own destructor in class, compiler creates a default destructor for us. The default destructor works fine unless we have dynamically allocated memory or pointer in class. When a class contains a pointer to memory allocated in class, we should write a destructor to release memory before the class instance is destroyed. This must be done to avoid memory leak.

# Can a destructor be virtual?
Yes, In fact, it is always a good idea to make destructors virtual in base class when we have a virtual function.
Deleting a derived class object using a pointer to a base class that has a non-virtual destructor results in undefined behavior. To correct this situation, the base class should be defined with a virtual destructor.

```
// A program with virtual destructor 
#include<iostream> 

using namespace std; 

class base { 
public: 
	base()	 
	{ cout<<"Constructing base \n"; } 
	virtual ~base() 
	{ cout<<"Destructing base \n"; }	 
}; 

class derived: public base { 
public: 
	derived()	 
	{ cout<<"Constructing derived \n"; } 
	~derived() 
	{ cout<<"Destructing derived \n"; } 
}; 

int main(void) 
{ 
derived *d = new derived(); 
base *b = d; 
delete b; 
getchar(); 
return 0; 
} 
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 5. What are the basic concepts of OOPs?

The basic concepts of OOPs are:
1. Encapsulation
2. Polymorphism
3. Inheritance
4. Abstraction
----------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
# 6. What is Encapsulation? - https://www.geeksforgeeks.org/encapsulation-in-c/

Encapsulation is defined as wrapping up of data and information under a single unit. In Object Oriented Programming, Encapsulation is defined as binding together the data and the functions that manipulates them.
Encapsulation is an OOPs concept to create and define the restrictions and permissions of an object and its member variable and methods. It is very simple to explain the concept is to make the member variables of a class private and providing public getter and setter methods.
Encapsulation also lead to data abstraction or hiding. As using encapsulation also hides the data

```
// c++ program to explain Encapsulation 

#include<iostream> 
using namespace std; 

class Encapsulation 
{ 
	private: 
		// data hidden from outside world 
		int x; 
		
	public: 
		// function to set value of 
		// variable x 
		void set(int a) 
		{ 
			x =a; 
		} 
		
		// function to return value of 
		// variable x 
		int get() 
		{ 
			return x; 
		} 
}; 
int main() 
{ 
	Encapsulation obj; 
	
	obj.set(5); 
	
	cout<<obj.get(); 
	return 0; 
} 
```
In the above program the variable x is made private. This variable can be accessed and manipulated only using the functions get() and set() which are present inside the class. Thus we can say that here, the variable x and the functions get() and set() are binded together which is nothing but encapsulation.

----------------------------------------------------------------------------------------------------------------------------------------------------------------
# 7. What are the access modifiers? - https://www.geeksforgeeks.org/access-modifiers-in-c/

Access modifiers define the scope of the method or variable that can be accessed from other various objects.
Access modifiers are used to implement an important feature of Object-Oriented Programming known as Data Hiding.
There are 3 types of access modifiers available in C++:

Public
Private
Protected

# Public: 
All the class members declared under public will be available to everyone. The data members and member functions declared public can be accessed by other classes too. The public members of a class can be accessed from anywhere in the program using the direct member access operator (.) with the object of that class.
# Private: 
The class members declared as private can be accessed only by the functions inside the class. They are not allowed to be accessed directly by any object or function outside the class. Only the member functions or the friend functions are allowed to access the private data members of a class.
# Protected:
Protected: Protected access modifier is similar to that of private access modifiers, the difference is that the class member declared as Protected are inaccessible outside the class but they can be accessed by any subclass(derived class) of that class.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 8. What is Polymorphism? - https://www.geeksforgeeks.org/polymorphism-in-c/
The word polymorphism means having many forms. In simple words, we can define polymorphism as the ability of a message to be displayed in more than one form.

# 9. Define overloading and overriding in OOPs?

Overloading is static binding, whereas overriding is productive binding. Overloading is the same method with different arguments, and it may or may not return the equal value in the same class itself.
Overriding is the same method names with the same arguments and return types identified with the class and its child class.


# 10. What are all the operators that cannot be overloaded?

The operators that cannot be overloaded are:

Member Selection
Scope Resolution
Member selection through a pointer to a function

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------# 

# In C++ polymorphism is mainly divided into two types:

Compile time Polymorphism
Runtime Polymorphism

![polymorphism](https://media.geeksforgeeks.org/wp-content/uploads/20200703160531/Polymorphism-in-CPP.png)

# Compile time Polymorphism
This type of polymorphism is achieved by function overloading or operator overloading.

## Function Overloading:
When there are multiple functions with same name but different parameters then these functions are said to be overloaded. Functions can be overloaded by change in number of arguments or/and change in type of arguments.
```
// C++ program for function overloading 
#include <bits/stdc++.h> 

using namespace std; 
class Krishna
{ 
	public: 
	
	// function with 1 int parameter 
	void func(int x) 
	{ 
		cout << "value of x is " << x << endl; 
	} 
	
	// function with same name but 1 double parameter 
	void func(double x) 
	{ 
		cout << "value of x is " << x << endl; 
	} 
	
	// function with same name and 2 int parameters 
	void func(int x, int y) 
	{ 
		cout << "value of x and y is " << x << ", " << y << endl; 
	} 
}; 

int main() { 
	
	Krishna obj1; 
	
	// Which function is called will depend on the parameters passed 
	// The first 'func' is called 
	obj1.func(7); 
	
	// The second 'func' is called 
	obj1.func(9.132); 
	
	// The third 'func' is called 
	obj1.func(85,64); 
	return 0; 
} 

```
In the above example, a single function named func acts differently in three different situations which is the property of polymorphism.

## Operator Overloading: https://www.geeksforgeeks.org/operator-overloading-c/
C++ also provide option to overload operators. For example, we can make the operator (‘+’) for string class to concatenate two strings. We know that this is the addition operator whose task is to add two operands. So a single operator ‘+’ when placed between integer operands , adds them and when placed between string operands, concatenates them.
```
// CPP program to illustrate Operator Overloading 
#include<iostream> 
using namespace std; 

class Complex { 
private: 
	int real, imag; 
public: 
	Complex(int r = 0, int i =0) {real = r; imag = i;} 
	
	// This is automatically called when '+' is used with 
	// between two Complex objects 
	Complex operator + (Complex const &obj) { 
		Complex res; 
		res.real = real + obj.real; 
		res.imag = imag + obj.imag; 
		return res; 
	} 
	void print() { cout << real << " + i" << imag << endl; } 
}; 

int main() 
{ 
	Complex c1(10, 5), c2(2, 4); 
	Complex c3 = c1 + c2; // An example call to "operator+" 
	c3.print(); 
} 

```
In the above example the operator ‘+’ is overloaded. The operator ‘+’ is an addition operator and can add two numbers(integers or floating point) but here the operator is made to perform addition of two imaginary or complex numbers. 

## operators that cannot be overloaded.
```
   . (dot) 
   :: 
   ?: 
   sizeof 
   ```
# Runtime polymorphism: https://www.geeksforgeeks.org/virtual-functions-and-runtime-polymorphism-in-c-set-1-introduction/
This type of polymorphism is achieved by Function Overriding.
Function overriding on the other hand occurs when a derived class has a definition for one of the member functions of the base class. That base function is said to be overridden.

```
// C++ program for function overriding 

#include <bits/stdc++.h> 
using namespace std; 

class base 
{ 
public: 
	virtual void print () 
	{ cout<< "print base class" <<endl; } 

	void show () 
	{ cout<< "show base class" <<endl; } 
}; 

class derived:public base 
{ 
public: 
	void print () //print () is already virtual function in derived class, we could also declared as virtual void print () explicitly 
	{ cout<< "print derived class" <<endl; } 

	void show () 
	{ cout<< "show derived class" <<endl; } 
}; 

int main() 
{ 
	base *bptr; 
	derived d; 
	bptr = &d; 
	
	//virtual function, binded at runtime (Runtime polymorphism) 
	bptr->print(); 
	
	// Non-virtual function, binded at compile time 
	bptr->show(); 

	return 0; 
} 

```
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 11.  What is inheritance and its types?

A subclass can inherit the behaviours and states of its superclass are known as inheritance. There are various types of inheritance:

Hybrid Inheritance
Multiple Inheritance
Single Inheritance
Multi-level Inheritance
Hierarchical Inheritance

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Inheritance - https://www.geeksforgeeks.org/inheritance-in-c/
The capability of a class to derive properties and characteristics from another class is called Inheritance.
Inheritance is one of the most important feature of Object Oriented Programming.

## Sub Class: 
The class that inherits properties from another class is called Sub class or Derived Class.
## Super Class:
The class whose properties are inherited by sub class is called Base Class or Super class.

# Why and When to use?

![condition](https://media.geeksforgeeks.org/wp-content/uploads/inheritance.png)
![Solution](https://media.geeksforgeeks.org/wp-content/uploads/inheritance2.png)

Using inheritance, we have to write the functions only one time instead of three times as we have inherited rest of the three classes from base class(Vehicle).

# Implementing inheritance in C++: 
For creating a sub-class which is inherited from the base class we have to follow the below syntax.
Syntax:
```
class subclass_name : access_mode base_class_name
{
  //body of subclass
};
```
# Access_mode
![Access Modifier](https://media.geeksforgeeks.org/wp-content/cdn-uploads/table-class.png)

# Types of Inheritance-

## 1. Single Inheritance-
In single inheritance, a class is allowed to inherit from only one class. i.e. one sub class is inherited by one base class only.
  
# Syntax -
```
class subclass_name : access_mode base_class
{
  //body of subclass
};
```
 ![single inheritance](https://media.geeksforgeeks.org/wp-content/uploads/single-inheritance.png)
```
// C++ program to explain  Single inheritance 
#include <iostream> 
using namespace std; 

// base class 
class Vehicle { 
public: 
	Vehicle() 
	{ 
	cout << "This is a Vehicle" << endl; 
	} 
}; 

// sub class derived from two base classes 
class Car: public Vehicle{ 

}; 

int main() 
{ 
	// creating object of sub class will 
	// invoke the constructor of base classes 
	Car obj; 
	return 0; 
} 

```

## 2. Multiple Inheritance: 
Multiple Inheritance is a feature of C++ where a class can inherit from more than one classes. i.e one sub class is inherited from more than one base classes.

Syntax:
```
class subclass_name : access_mode base_class1, access_mode base_class2, ....
{
  //body of subclass
};
```
![multiple](https://www.geeksforgeeks.org/multiple-inheritance-in-c/)

```
// C++ program to explain  multiple inheritance 
#include <iostream> 
using namespace std; 

// first base class 
class Vehicle { 
public: 
	Vehicle() 
	{ 
	cout << "This is a Vehicle" << endl; 
	} 
}; 

// second base class 
class FourWheeler { 
public: 
	FourWheeler() 
	{ 
	cout << "This is a 4 wheeler Vehicle" << endl; 
	} 
}; 

// sub class derived from two base classes 
class Car: public Vehicle, public FourWheeler { 

}; 

int main() 
{ 
	// creating object of sub class will 
	// invoke the constructor of base classes 
	Car obj; 
	return 0; 
} 

```
## 3. Multilevel Inheritance: 
In this type of inheritance, a derived class is created from another derived class.

![multilevel](https://media.geeksforgeeks.org/wp-content/uploads/multilevel-inheritance.png)

```
// C++ program to implement Multilevel Inheritance 
#include <iostream> 
using namespace std; 

// base class 
class Vehicle 
{ 
public: 
	Vehicle() 
	{ 
	cout << "This is a Vehicle" << endl; 
	} 
}; 
class fourWheeler: public Vehicle 
{ public: 
	fourWheeler() 
	{ 
	cout<<"Objects with 4 wheels are vehicles"<<endl; 
	} 
}; 
// sub class derived from two base classes 
class Car: public fourWheeler{ 
public: 
	car() 
	{ 
	cout<<"Car has 4 Wheels"<<endl; 
	} 
}; 

// main function 
int main() 
{ 
	//creating object of sub class will 
	//invoke the constructor of base classes 
	Car obj; 
	return 0; 
} 
```
## 4. Hierarchical Inheritance: 
In this type of inheritance, more than one sub class is inherited from a single base class. i.e. more than one derived class is created from a single base class.

![Hierarchical](https://media.geeksforgeeks.org/wp-content/uploads/hierarchical-inheritance.png)
```
// C++ program to implement Hierarchical Inheritance 
#include <iostream> 
using namespace std; 

// base class 
class Vehicle 
{ 
public: 
	Vehicle() 
	{ 
	cout << "This is a Vehicle" << endl; 
	} 
}; 


// first sub class 
class Car: public Vehicle 
{ 

}; 

// second sub class 
class Bus: public Vehicle 
{ 
	
}; 

int main() 
{ 
	// creating object of sub class will 
	// invoke the constructor of base class 
	Car obj1; 
	Bus obj2; 
	return 0; 
} 

```

## 5. Hybrid (Virtual) Inheritance: 
Hybrid Inheritance is implemented by combining more than one type of inheritance. For example: Combining Hierarchical inheritance and Multiple Inheritance.
Below image shows the combination of hierarchical and multiple inheritance:

![hybrid](https://media.geeksforgeeks.org/wp-content/uploads/Hybrid-Inheritance.png)

```
// C++ program for Hybrid Inheritance 

#include <iostream> 
using namespace std; 

// base class 
class Vehicle 
{ 
public: 
	Vehicle() 
	{ 
	cout << "This is a Vehicle" << endl; 
	} 
}; 

//base class 
class Fare 
{ 
	public: 
	Fare() 
	{ 
		cout<<"Fare of Vehicle\n"; 
	} 
}; 

// first sub class 
class Car: public Vehicle 
{ 

}; 

// second sub class 
class Bus: public Vehicle, public Fare 
{ 
	
}; 
int main() 
{ 
	// creating object of sub class will 
	// invoke the constructor of base class 
	Bus obj2; 
	return 0; 
} 

```
# A special case of hybrid inheritance : Multipath inheritance:
A derived class with two base classes and these two base classes have one common base class is called multipath inheritance. An ambiguity can arrise in this type of inheritance.

!{multipath](http://www.tutorialdost.com/Cpp-Programming-Tutorial/Images/Multipath-Inheritance-Ambiguity-In-Cpp.png)

```
// C++ program demonstrating ambiguity in Multipath Inheritance 

#include<iostream.h> 
#include<conio.h> 
class ClassA 
	{ 
			public: 
			int a; 
	}; 

	class ClassB : public ClassA 
	{ 
			public: 
			int b; 
	}; 
	class ClassC : public ClassA 
	{ 
			public: 
			int c; 
	}; 

	class ClassD : public ClassB, public ClassC 
	{ 
			public: 
			int d; 
	}; 

	void main() 
	{ 

			ClassD obj; 

			//obj.a = 10;				 //Statement 1, Error 
			//obj.a = 100;				 //Statement 2, Error 

			obj.ClassB::a = 10;	 //Statement 3 
			obj.ClassC::a = 100;	 //Statement 4 

			obj.b = 20; 
			obj.c = 30; 
			obj.d = 40; 

			cout<< "\n A from ClassB : "<< obj.ClassB::a; 
			cout<< "\n A from ClassC : "<< obj.ClassC::a; 

			cout<< "\n B : "<< obj.b; 
			cout<< "\n C : "<< obj.c; 
			cout<< "\n D : "<< obj.d; 

	} 

```

In the above example, both ClassB & ClassC inherit ClassA, they both have single copy of ClassA. However ClassD inherit both ClassB & ClassC, therefore ClassD have two copies of ClassA, one from ClassB and another from ClassC.
If we need to access the data member a of ClassA through the object of ClassD, we must specify the path from which a will be accessed, whether it is from ClassB or ClassC, bco’z compiler can’t differentiate between two copies of ClassA in ClassD.

# There are 2 ways to avoid this ambiguity:

Use scope resolution operator
Use virtual base class

### Avoiding ambiguity using scope resolution operator:

Using scope resolution operator we can manually specify the path from which data member a will be accessed, as shown in statement 3 and 4, in the above example.
```
obj.ClassB::a = 10;        //Statement 3 
obj.ClassC::a = 100;      //Statement 4 
```

Note : Still, there are two copies of ClassA in ClassD.

### Avoiding ambiguity using virtual base class:

```
#include<iostream.h> 
	#include<conio.h> 

	class ClassA 
	{ 
			public: 
			int a; 
	}; 

	class ClassB : virtual public ClassA 
	{ 
			public: 
			int b; 
	}; 
	class ClassC : virtual public ClassA 
	{ 
			public: 
			int c; 
	}; 

	class ClassD : public ClassB, public ClassC 
	{ 
			public: 
			int d; 
	}; 

	void main() 
	{ 

			ClassD obj; 

			obj.a = 10;	 //Statement 3 
			obj.a = 100;	 //Statement 4 

			obj.b = 20; 
			obj.c = 30; 
			obj.d = 40; 

			cout<< "\n A : "<< obj.a; 
			cout<< "\n B : "<< obj.b; 
			cout<< "\n C : "<< obj.c; 
			cout<< "\n D : "<< obj.d; 

	} 
```

According to the above example, ClassD has only one copy of ClassA, therefore, statement 4 will overwrite the value of a, given at statement 3.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 12. What is Abstraction?

Abstraction is an OOPs approach to construct the structure of the real-world objects. During the construction, only the general states and behaviours are taken, and more specific states and actions are left aside for the implementers.


# 13. What does the keyword virtual represented in the method definition?

It represents that we can override the method.

# 14. What is Static Binding and Dynamic Binding?

Static Binding is a binding in which name can be combined with the class during collection time, and it is also called as early binding.

Dynamic Binding is a binding in which name can be identified with the class during execution time, and it is also known as Late Binding

# 15. What is an abstract class?

An abstract class cannot be proved. Formation of an object is not possible with an abstract class, but it can be inherited. An abstract class can only contain an abstract method, and java allows only abstract method in abstract class while other languages allow non-abstract method as well.



