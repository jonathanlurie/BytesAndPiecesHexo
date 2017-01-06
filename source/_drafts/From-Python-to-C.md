---
title: From Python to C++
photos:
  - cover.jpg
tags:
- code
---

Swimming upstream: a C++ cheatsheet for Python coders

<!--more-->
![](cover.jpg)

To most programmers, especially from the new generation, C++ is not the most common language. It is not an easy language, some might even say it is *tricky*. The following is more a *cheat-sheet* than a tutorial, and reviews some of the key disparities between C/C++ and other modern languages such as Python, Javascript or PHP. Those differences take place in form (syntax) but also in concept and will change to way a programmer has to deal with data and processes. Of course, it would be impossible to make an exhaustive list of differences since C++, like every language, comes with its bunch of subtlety, so we will focus on the most obvious ones.

# Why using C++?
The first and most important reason is speed. C/C++ is way faster than other languages. This relies in the fact that C++ is a *low level* language, compiled into a series of instruction directly understandable by the machine (and some humans, thanks to assembly).  
We could use the translator analogy: if you need to talk to a person who is not from the same country, it's easier if both of you speak a common language, even though it is the mother tongue of none of you (Esperanto, someone?). If both speak Esperanto fluently, the conversation will be fast and clear (case 1). In other case, you will need an interpreter who knows well both mother tongues. It's better than nothing to understand each other but it's not as fast and might lead to simplifications. Well, C/C++ is *case 1* and Python/JS/PHP are *case 2*.

Most of the time, **you won't need C++**, but if you have large datasets, be curious and read on!

## First thing first
As you may know, JS is quite an exception in the *Object Oriented* language family, since everything is kind of an object and kind of a function at the same time. Of course you can play with *prototypes* to reach *OOP* paradigm but in the following examples, I'd rather choose Python as a reference for a *high level* programming language. I hope JS aficionados won't mind.

## Entry point
In Python, you can start to code directly by writing succesive instruction into a .py file, just like that:

```python
# content of myCode.py

herName = "Barbie"
hisName = "Ken"
greetings = "hello " + herName + " and " + hisName " !"
print(greetings)
```

In C++, you have to setup a basic structure, and it starts by the entry point of you program. The *main* function:

```cpp
int main() {
  // doing some stuff
  ...
  ...

  // finishing with a return
  return 0;  
}
```

Some C/C++ program does not have a `main` function, meaning they do not have any entry point: libraries. Libraries is not what we will talk about on the following, so we will assume that all C++ example have a starting point.

## Types, variables and constants
In C++, typing is **strong**! What does it mean? Well, simply that you have to know what kind of data you will need before using it, and stick to it.

**Python:**
```python
# You just need to declare a number variable
myNumber = 12

# Later, you realize you need floating precision. With Python, no problem
myNumber = 13.49

# At certain point, you are not really sure what you want, so myNumber becomes a string
myNumber = "one and a half"
```

**C++:**
```cpp
// You want an integer, first, you have to declare its type
int myNumber = 12;

// You want to add more precision so you think of that (from your old Py habits)
myNumber = 13.49;
```
Since you declared `myNumber` as a `int`, its value will be automatically *casted* to integer when associated with the value `13.49`, like a simple truncate, **`myNumber` equals 13**. Still, the compiler is not happy about it (we'll see later what compilation is). We get a warning message:

```shell
warning: implicit conversion from 'double' to 'int' changes value from 12.5 to 12 [-Wliteral-conversion]
        myNumber = 12.5;
                 ~ ^~~~
```
Such *warning* does not block the compilation, so we will be able to launch our program.

Even though it is not the most academic way to do, most developers use this to get rid of the floating part of a number. This is more or less equivalent to this pythonic cast:

**Python:**
```python
# first time declaration
myNumber = 13.49;

# casting it to integer
myInteger = (int)myNumber
# myInteger here is 13
```

We have seen that Python typing is so weak that a variable could change its content even to a string (but also an array, list, etc.). Let's see what happens when we try that in C++:

```cpp
int myNumber = 10;
myNumber = 12.5;
myNumber = "one";
```
It is impossible to run this piece of code, because it is impossible to compile it . Instead, we have a nice message:

```shell
error: assigning to 'int' from incompatible type 'const char [4]'
        myNumber = "one";
                 ^ ~~~~~
```

### Fundamental types in C++
Here are the most common ones:
  - int: signed integer, from -2147483648 to 2147483647
  - float : signed number with decimals, from +/- 3.4e +/- 38 (~7 digits)
  - double : same as float but with a wider range a larger precision +/- 1.7e +/- 308 (~15 digits)
  - char : one character declared between simple quotes ('a') or a number from -127 to 127

The numerical values can be flavored with `long` to increase the range, or with `unsigned` to shift the accessible range of range of a type to only positive values.

**C++:**
```cpp
// a char
char littleNumber = -13; // could be any of [-127; +127]

// an unsigned char
unsigned char littlePositiveNumber = 200; // could be any of [0; +255]
```
For more information on types and their range, check [this table by TutorialPoints](http://www.tutorialspoint.com/cplusplus/cpp_data_types.htm).  

So what if we want a string longer than one character? In Python, we have:

**Python:**
```python
myString = "hello there"
```

And in C++, we have different way to do that.  
The old C style way, using an array of characters, declared with the * (asterisk) or [] (square bracket) operators:

**C, also works on C++:**
```cpp
// We create an array of char of unknown size
char* myString = "hello there";

// this is the same as
char myString2[] = "hello there";

// of with a maximum size known in advance:
char myString3[15] = "hello there";
```
In those cases, the compiler will place a `'\0'` character at the end of your strings, so that you may be able to find the end. Because **an array of char does not know its own size!**

In modern C++, we have easier ways to deal with strings, thanks to the *standard library* (we'll come to that later):

```cpp
// we first need to include the standard library (std)
#include <iostream>

// we state that we will be using the standard library (std)
using namespace std;

int main() {
    // decalring a C++ string
	string myString = "hello there";
	string mySecondString = "how are you?";

	// print it on the standard output (terminal)
	cout << myString << " " << mySecondString << endl;

	return 0;
}
```

The Python equivalent of that would be:
```python
if __name__ == "__main__":
  myString = "hello there";
  mySecondString = "how are you?";
  print(myString + " " + mySecondString)
```

Knowing how to use char* is a *mandatory* for C/C++ coders, event though more modern alternative exists. They are still used by a most of programmer, not because they are nostalgic but because it can be very convenient to use.

### The const thing
In Python, there is no way to declare a variable and to make sure that its value will remain as declared. In C++, `const` is a reserved word for that, and if later in you code you try to change a *const variable* value, you will hear about it! As shown below:

**C++:**
```cpp
// const values are usually writen with capital letters, but it's not mandatory
const int PI = 3.1415;

// now, we try to change PI
PI = 23.2;
```

During the compilation, we will get a nice **ERROR**:

```shell
error: read-only variable is not assignable
        PI = 23.2;
        ~~ ^
```
Is also considered `const` all values that may be assign 'on the fly'. Example:

```cpp
int num1 = 12;
int num2 = num1 + 32;
```
Here, `32` (alone) can be considered as `const`, simply because `32` is `32` and cannot be changed. But this is more obvious when casting strings.

There are other cases where `const` is useful, like when used in function arguments or return type but we'll see that later.

## Casting from a type to another (and how to deal with Strings)
### Numbers
As we have seen before, we can cast a variable using the desired type:

**C++:**
```cpp
float floatNumber = 12.45;

// implicit cast, forced by the receiver:
int aInteger = floatNumber; // is 12

// Explicit cast, due to conversion (old C style):
int aSecondInteger = (int)floatNumber; // is 12

// explicit cast, due to conversion (old C style):
float aTruncatedFloat = (int)floatNumber; // is 12. still a float
```
As you see, this is very similar to Python, but this is actually C-style casting and not C++.

In C++, there are (mostly) one ways to cast from a type to another: `static_cast`. Here is the syntax:

**C++:**
```cpp
float myNumber = 2.987;
float casted1 = static_cast<int>(myNumber); // is 2.
```
You may have heard of `dynamic_cast` but it is reserved for complex object casting in the context of inheritance, not for simple types.

On the section **Inheritance and interface** we will learn more about how to use `static_cast` and `static_cast` with complex objects.

### strings
We know `char`, `char* `and `string` but we don't really know how to go from one to another.

```cpp
// declaring a C++ string
string myCppStr = "hello cpp";

// declaring a C-style string
char myCstr[] = "hello c";
char myCstr2[] = " good bye c";

// assigning, with an implicit cast
string myCppFromC = myCstr; // myCppFromC is "hello c"
```

But if you want `myCppFromC` to be a concatenation of multiple C-style string, you cannot rely on *implicit casting*, you have to convert your C-style strings (char*) for real. The best way is to use the `string()` constructor:

```cpp
char myCstr[] = "hello c...";
char myCstr2[] = " good bye c";

string myCppFromC = string(myCstr) + string(myCstr2); // is "hello c...  good bye c"
```

Now, in order to use some libraries or functions that takes only C-style string as argument, you must convert your C++-style string into char*. Hopefully, the `string`class has something for that:

```cpp
string myCppStr = "hello cpp";

// [1] converting it to a const char* (you won`t be able to modify it)
const char* cstrConst = myCppStr.c_str();

// [2] converting to a regular char*
char *cstrNotConst = &myCppStr[0u];
```
Since `const` does not exist in Python, we wouldn't bother with the difference between solution [1] and [2], but here, it has its importance. Let's try to understand better what means solution [2]:
  - `&` means you are accessing the myCppStr string by its address
  - `0u` means *unsigned 0*, because yes, C/C++ makes the difference between +0 and -0

You may ask: "Why does it return the entire string and not only the 'h' character?" C++ assumes that you are working with a string, so instead of returning only the first character ("h"), it returns the whole thing until it finds the '\0' ending character (which is invisible on the standard output).

### Number to strings
In Python, converting numbers to string is pretty strainghtforward and often needed in case of printing:

```python
aNumber = 12.4
aSecondNumber = 23
theResult = "my numbers are " + str(aNumber) + " and " + str(aSecondNumber)
print(theResult)
```
Strangely, even thought Python uses *weak typing*, casting form numbers to string is still mandatory. In C++ you will have to use an intermediate type to be able to concatenate numbers with strings, `ostringstream` (oss):

```cpp
#include <iostream> // standard library
#include <sstream> // standard lib extension
using namespace std;

int main () {
  ostringstream theOss;

  string str1 = "a regular string";
  float aNumber = 23.7;
  int anotherNumber = 98;

  // concatenating everything
  theOss << str1 << " " << aNumber << anotherNumber << " the end.";

  // printing the output
  std::cout << theOss.str() << endl; // is "a regular string 23.798 the end."

  // reseting this oss
  theOss.str("");

  // printing again
  std::cout << theOss.str() << endl; // is "" (empty)

  return 0;
}
```
It is pretty common to see the same *oss* being used several times for a different purposes. Most of the time, they act like a handy tool more than for really storing data.


## The standard library

## Limit of scope {}

## Functions

## if, for, while, do, switch

## Order of declaration

## Pointers and references (and what is this & operator?)
from http://stackoverflow.com/questions/10789740/passing-stdstring-by-value-or-reference
There are multiple answers based on what you are doing with the string.

1. Using the string as an id (will not be modified). Passing it in by const reference is probably the best idea here: (std::string const&)

2. Modifying the string but not wanting the caller to see that change. Passing it in by value is preferable: (std::string)

3. Modifying the string but wanting the caller to see that change. Passing it in by reference is preferable: (std::string &)

4. Sending the string into the function and the caller of the function will never use the string again. Using move semantics might be an option (std::string &&)



## Modify a variable with a function

## Losing variables (in outa scope)

## Arrays and freeing memory
In Python like in C++, array is kind a the to-go container. Still, the comparison stops here. The following list show how C++ arrays are different:
  - It needs to be instantiated with its final size
  - C++ being *strong typed*, an array can only contain one type of data
  - An array does not know its own size. This information has to be stored somewhere
  - An element of an array does not know its position within the array (not even if it is the first)
  - An array has to be explicitly deleted to free the memory, except for static arrays. There is no garbage collection mechanism in C++
  - *Array* is not an object in C++, in conclusion, there is no associated methods (removing an element, easy slicing, adding an element in the middle, etc.)

So yes, compared to Python, C++ arrays are really boring to use! But here is how to declare a static array:

```cpp
// we already know the elements that compose our array,
// this is static array:
int anIntArray[] = {0, 1, 3, 5, 7};

// we cannot ad elements, but we can change them:
anIntArray[1] = 12; // is now {0, 12, 3, 5, 7};

// since it's static, no need to delete it, it will die
// at the end of this scope.
```
Still, most of the time, you don't know in advance what values will populate your array, then you have to use a dynamic array:

```cpp
// One line decalration of a 10 element array
int *anArray = new int[10];

// then you can fill it:
array[8] = 986;

// When you are done, you MUST free the memory:
delete[] anArray;
// reset the pointer
anArray = 0;

// in some case, it is convenient to declare the array
// and later determine its size:
int *anotherArray = 0;
// do something
...
// allocate the space:
anotherArray = new int[10];
...
delete[] anotherArray;
// reset the pointer
anotherArray = 0;
```
Reseting the pointer `anotherArray = 0;` is not mandatory and you code will work perfectly if you don't do so. BUT, it is part of the *good practices* and sometimes very useful when you use an array, delete it, allocate it again and so on. This will help you to know if your array is being used right now or not:

```cpp
int *anArray =0;

while(anyCondition){
  anArray = new int[10];

  // do something
  ...

  if(anArray){
    // do something if your array is instanciated
  }else{
    // do something if your array is NOT instanciated
  }

  if(wateverCondition){
    // When you are done, you MUST free the memory:
  delete[] anArray;
    // reset the pointer
    anArray = 0;
  }

  // do something
  ...

}
```
In this example, hopefully you wrote `anArray = 0;` after deleting the array, otherwise you wouldn't know if it contains data or not.

### Using arrays as arguments of functions

### Using arrays as return values of functions

## Other containers and equivalents in Python (cf. templates)

## Class and object

## Inheritance and interface

### Casting from top to base
http://www.cplusplus.com/doc/tutorial/typecasting/

## Templates

## Tricks your can't do in Python
Bit masks, bit shifts

## Working with several files (cf. order of declaration)

## Compilation and optimization

## working with external libraries and linking

# Source
[Tutorial point C++](http://www.tutorialspoint.com/cplusplus/cpp_data_types.htm)
[cast in C++](http://stackoverflow.com/questions/332030/when-should-static-cast-dynamic-cast-const-cast-and-reinterpret-cast-be-used)
[cast in C++ from the reference](http://www.cplusplus.com/doc/tutorial/typecasting/)
[Pass an arg with reference](http://stackoverflow.com/questions/10789740/passing-stdstring-by-value-or-reference)
