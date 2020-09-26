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

(I don't believe this subject was actually covered in this chapter and it is probably a holdover from edition 1 of the book.) Inline functions are functions that are copied into memory at each location where they are called. This makes them faster to access since there is no search for them as they are called. However, because they are copied throughout the code, they can cause massive expansion of the code base and lead to a glut of code. Current compliers decide for you if the function should be inline and it is so much a choice of the user. More detailed explanations: [1](https://www.cplusplus.com/articles/2LywvCM9/), [2](https://stackoverflow.com/questions/1759300/when-should-i-write-the-keyword-inline-for-a-function-method#:~:text=C%2B%2B%20inline%20function%20is%20powerful,is%20called%20at%20compile%20time.&text=The%20compiler%20can%20ignore%20the,is%20more%20than%20a%20line.)

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
* Rational(const IntType & numerator, const IntType denominator), n = 4, d =3
* Declares a function, will error out as no function is present
* Rational(const IntType & numerator, const IntType denominator), Pointer to Rational object that has the fields n = 4, d = 3
* Rational(const IntType & numerator = 0), Pointer to Rational object that has the fields n = 5, d = 1
* 5x Rational(const IntType & numerator = 0), Pointer to array that has five Rational objects all with the fields n = 0, d = 1
* 10x Rational(const IntType & numerator = 0), Pointer to vector that has ten Rational objects all with the fields n = 0, d = 1
* May cause an error as the form k[10] is not a method for initializing a vector. It is a way of pulling an element out of an existing vector.

2.12

When these variables are no longer needed, they must be explicitly deleted.

2.13

sizeof() includes the memory consumed by private members in the value returned

2.14

In this situation, nothing in the class would be useable. It would just be a locked box.

2.15

If the rhs parameter is passed by value, then the complier would first make one copy of the object to get the value and then make a second copy of the object to do the operation.

2.16

<ol type="a">
  <li>Because all of the constructors use the reduce function and the numer and denom are not accessible outside of the class, we can simply use:

```
bool Rational::operator== (const Rational & rhs) const
{
  return numer == rhs.numer && denom == rhs.denom;
}
```

and 

```
bool Rational::operator!= (const Rational & rhs) const
{
  return !(&rhs == this);
}
```

  </li>
  <li> The values don't need to be reduced at the end of this function because the original rational is reduced and by reducing the Rationals with the denominators flipped we are doing all of the reduction that is possible.

```
Rational Rational::operator*(const Rational & rhs) const
{
  Rational newLhs = Rational(numer, rhs.denom);
  Rational newRhs = Rational(rhs.numer, denom);
  newLhs *= newRhs;
  return newLhs;
}
```

  </li>
  <li></li>
  <li>

```
Rational Rational::operator^( int rhs ) const {
  Rational *copyRational = new Rational(*this);
  for (int i = 1; i < rhs; i++) {
    copyRational->numer *= numer;
    copyRational->denom *= denom;
  }
  return *copyRational;
}
```

  </li>
</ol>

2.17



2.18
<ol type="a">
  <li>string</li>
  <li>

```
string string::substring( int startIndex, int endIndex ) const
{
    if( startIndex < 0 )
        throw StringIndexOutOfBoundsException( startIndex, length( ) );
    if ( endIndex >= strLength )
        throw StringIndexOutOfBoundsException( endIndex, length( ) );
    string substring;
    for (int i = startIndex; i < endIndex; i++)
    {
        substring += buffer[i];
    }
    return substring;
}
```

  </li>
  <li> The first one will declare a string and assign it immediately. The second will create a null string variable and then do a copy of the substring into that variable.
</ol>

2.19
<ol type="a">
  <li>It will not be caught by the complier since it will be treated as an implicit conversion</li>
  <li>

`string( char ch )` and `const string & operator+=( const string & rhs );`
  </li> 
</ol>

2.20

```
string::string( int bufferSize ) 
{
  if (bufferSize > 0)
    buffer = new char [ bufferSize ];
  else
    buffer = new char [0];
}
```

When a bufferSize of zero is passed through, the string initializes, but is essentially a pointer to a single bit that is empty.
