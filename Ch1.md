1.1
* ptr++: increments - makes the pointer point to the next address after the current one
* ptr--: decrements - makes the pointer point to the address previous to the current one
* *ptr: gets the value that is at the pointer's address
* &ptr: passes the pointer by reference
* delete ptr: removes the pointer and resets the value at the address it occupied

1.2
<ol type="a">
  <li>This code is legal. It will initialize two int variables (a & b), a pointer variable (ptr), and a pointer to a pointer variable (ptrPtr). The pointer variable is then set to the address of the variable 'a' and the pointer to the pointer is set to the address of ptr.</li>
  <li>*ptr and **ptrPtr => undefined (since a is not defined)</li>
  <li>Add the line
  
  `*ptrPtr = &b`
  
  </li>
  <li>ptr was declared as a pointer to an int object and ptrPtr was declared as a pointer to a pointer of an int object. Therefore, ptrPtr and ptr are different types and one cannot be assigned to the other</li>
</ol>

1.3
<ol type="a">
  <li>Yes. 
    <ul>
      <li>If x is a pointer, the &x will get the address the pointer lives at and then the * will get the value at that address (the original pointer).</li>
      <li>If x is an object, the &x will get the address the object lives at and then the * will get the value at that address (the original object).</li>
    </ul>
  </li>
  <li>Yes.
    <ul>
      <li>If x is a pointer, the *x will get the value of the object the pointer is pointing to and then the & will get the address the object lives at (the original pointer).</li>
      <li>If x is an object, the *x is not meaningful since x is not an address and, therefore, cannot be dereferenced.</li>
    </ul>
  </li>
</ol>

1.4
<ol type="a">
  <li>The address of a</li>
  <li>5</li>
  <li>Compliation error - a pointer and an int are not the same type and cannot be compared</li>
  <li>True</li>
  <li>Address of where the pointer is stored</li>
  <li>Compliation error - the object 'a' cannot be dereferenced since it is not a pointer</li>
  <li>5</li>
  <li>5</li>
</ol>

1.5
<ol type="a">
  <li>Makes a structure with an int variable and a pointer to another S structure</li>
  <li>Instantiates an instance of S</li>
  <li>Instantiates a pointer to the address of an object of type S (for now, it is Null)</li>
  <li>Initializes a vector with ten elements of type S</li>
  <li>Initializes a vector with ten pointers to elements of type S</li>
  <li>Returns the value of the 'a' member of the strucuture that the pointer, x, is pointing to</li>
  <li>Returns the address the pointer 'b' is pointing to for structure x</li>
  <li>Returns the address that member 'b' on structure z is pointing to</li>
  <li>Returns the value of the member 'a' on structure z</li>
  <li>Illegal. z is not a pointer and so performing the * operator on it causes the code to error</li>
  <li>Illegal. z is not a pointer and so performing the * operator on it causes the code to error</li>
  <li>Returns the pointer 'b' from the pointer x. z.b returns the pointer 'b' from the struct z. The '-' gets the difference between the addresses of these two pointers</li>
  <li>Illegal. y is a vector and has no member 'b'</li>
  <li>Returns the second element in the vector, y.</li>
  <li>Returns the member 'a' for the second element in the vector, y.</li>
  <li>Returns the member, pointer 'b' for the second element in the vector, y.</li>
  <li>Returns the third pointer in the vector, u.</li>
  <li>Gets the value at the address the third pointer in the vector, u, is pointing at</li>
  <li>Gets the member 'a' of the S-type value at the address of the third pointer in the vector, u</li>
  <li>Gets the member, pointer 'b' of the S-type value at the address of the third pointer in the vector, u</li>
  <li>Returns 0 since this value exceeds the limit of the vector</li>
  <li>Creates a reference to z. i.e. - the address that the value z is stored at</li>
  <li>Creates a reference to x. i.e. - the address that the pointer x is stored at</li>
  <li>Returns the vector, u</li>
  <li>Returns the vector, y</li>
</ol>

1.6
<ol type="a">
  <li>
      a = 3 </br>
      
      a -> [3]
      
  </li>
  <li>
      a = 3 </br>
      b = 3 </br>
      
      a -> [3] <- b
      
  </li>
  <li>
      a = 3 </br>
      b = 3 </br>
      c = 3 </br>
      
      a -> [3] <- b
            ^
            c
      
  </li>
</ol>
