2.1

Information hiding is when a class keeps private fields and/or methods that cannot be retrieved outside of the class (with the exception of friends). Encapsulation describes how classes hold onto the methods and fields that they own and are self-contained. C++ is an object oriented language, so it has objects instantiated from classes. These classes encapsulate all of the information and methods needed for the object.

2.2

The public section of the class holds onto all of the fields and methods that can be used by objects of other types that have initialized an instance of the class. The private section of the class holds onto all of the fields and methods that are inaccessable for objects of any other type.

2.3

A constructor sets up the initial state of an object. The destructor is called when an object is deleted or goes out of scope. It clears out and frees up the memory used by the fields for the object.

2.4

An object initialized using a copy constructor will have the form 

```
ClassName object = new ClassName(otherObject);
```

Whereas an object initialized using a copy assignment operator will have the form 

```
ClassName object = otherObject;
```

An object made from a copy constructor will take the information from the object being copied, but create a unique memory address for this object. The object initialized using a copy assignment operator will point to the same location in memory as the object being copied.

[A more thorough explanation](https://www.tutorialspoint.com/copy-constructor-vs-assignment-operator-in-cplusplus#:~:text=The%20Copy%20constructor%20and%20the,not%20make%20new%20memory%20space.)

2.5

C++ automatically creates a default constructor and destructor for each class that does not have one implemented. These may not be optimal, however.

2.6

If none of a class' fields are pointers, it is acceptable to use the default destructor, copy assignement operator, and copy constructor.

2.7

2.8

The ., *, ?:, and sizeof operators cannot be overloading

2.9

A friend function is a function that is allowed to access private members of the class it is declared a friend within.

2.10

A friend declaration can be made for the input and output functions. These declarations have to be in the public section of the class to be usable. Alternatively, objects can be made without using a friend declaration with a few adjustments. A new object can be created based on input by passing the input fields through via the constructor. If a print method which returns a string representation of the object is added to the class, then an output method can call this function.

2.11
* Rational(const IntType & numerator = 0), n = 0, d = 1
* Rational(const IntType & numerator = 0), n = 3, d = 1
* Rational(const IntType & numerator, const IntType denominator), n = 4, d = 3
* Rational(const IntType & numerator = 0), n = 0, d = 1
* 
* Declares a function, will error out as no function is present
* Rational(const IntType & numerator, const IntType denominator), Pointer to Rational object that has the fields n = 4, d = 3
* Rational(const IntType & numerator = 0), Pointer to Rational object that has the fields n = 5, d = 1
* 5x Rational(const IntType & numerator = 0), Pointer to array that has five Rational objects all with the fields n = 0, d = 1
* 10x Rational(const IntType & numerator = 0), Pointer to vector that has ten Rational objects all with the fields n = 0, d = 1
* May cause an error as the form k[10] is not a method for initializing a vector. It is a way of pulling an element out of an existing vector.

2.12

2.13

sizeof() includes the memory consumed by private members in the value returned
