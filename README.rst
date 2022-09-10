.. sectnum::

===============================================================================
C++ crash course for X programmers
===============================================================================
:Author: `FarazJalili <https://www.linkedin.com/in/faraz-jalili-80a08669/>`_

.. contents::
   :local:
   :depth: 2
   
   
Fundamental
===============================================================================


Input/Output
------------

Prefer the use of ``<iostream>`` for input/output operations (see stream
section for explanation).

.. code:: c++

   #include <iostream>
   using namespace std;
   int main (int argc, char **argv)
   {
       int i;
       cout << "Please enter an integer value: ";
       cin >> i;
       cout << "The value you entered is " << i  << endl;
       return 0;
   }

   
   
The C++ ``getline()`` is a standard library function that is used to read a string or a line from an input stream. It is a part of the ``<string>`` header. The ``getline()`` function extracts characters from the input stream and appends it to the string object until the delimiting character is encountered.

.. code:: c++

   #include <iostream>
   #include <string>
   using namespace std;
   int main (int argc, char **argv)
   {
        string mystr;
        cout << "What's your name? (press $ to complete): ";
        getline (cin, mystr, '$');
        cout << "Hello " << mystr << ".\n";
        cout << "What is your favorite team? ";
        getline (cin, mystr);
        cout << "I like " << mystr << " too!\n";
        return 0;
   }

New/Delete
----------

The ``new`` and ``delete`` keywords are used to allocate and free memory. They
are "object-aware" so you'd better use them instead of ``malloc`` and
``free``. In any case, never cross the streams (new/free or malloc/delete).

.. code:: c++

   int *a = new int;
   delete a;

   int *b = new int[5];
   delete [] b;

``delete`` does two things: it calls the destructor and it deallocates the
memory.

The ``malloc()`` function in C++ allocates a block of uninitialized memory to a pointer. It is defined in the cstdlib header file.

.. code:: c++

   #include <iostream>
   #include <cstdlib>
   using namespace std;

   int main() {

     // allocate 5 int memory blocks
     int* ptr = (int*) malloc(5 * sizeof(int));

     // check if memory has been allocated successfully
     if (!ptr) {
       cout << "Memory Allocation Failed";
       exit(1);
     }

     cout << "Initializing values..." << endl << endl;

     for (int i = 0; i < 5; i++) {
       ptr[i] = i * 2 + 1;
     }
     cout << "Initialized values" << endl;

     // print the values in allocated memories
     for (int i = 0; i < 5; i++) {

       // ptr[i] and *(ptr+i) can be used interchangeably
       cout << *(ptr + i) << endl;
     }

     // deallocate memory
     free(ptr);
     /* prints a garbage value after ptr is free */
     cout << "Garbage Value" << endl;

     for (int i=0; i<5; i++)
     {
        cout << *(ptr+i) << " ";
     }

     return 0;
   }

References
----------

A reference allows to declare an alias to another variable. As long as the
aliased variable lives, you can use indifferently the variable or the alias.

.. code:: c++

   int x;
   int& foo = x;

   foo = 42;
   std::cout << x << std::endl;

References are extremely useful when used with function arguments since it
saves the cost of copying parameters into the stack when calling the function.



TIPS
===============================================================================


Passing By Pointer Vs Passing By Reference
------------------------------------------

Passing by Pointer: Here, the memory location of the variables is passed to the parameters in the function, and then the operations are performed.

.. code:: c++

   #include <iostream>
   using namespace std;

   void swap(int *x, int *y)
   {
       int z = *x;
       *x = *y;
       *y = z;
   }

   // Driver Code
   int main()
   {
       int a = 45, b = 35;
       cout << "Before Swap\n";
       cout << "a = " << a << " b = " << b << "\n";

       swap(&a, &b);

       cout << "After Swap with pass by pointer\n";
       cout << "a = " << a << " b = " << b << "\n";
       return 0;
   }


Passing by Reference: It allows a function to modify a variable without having to create a copy of it. We have to declare reference variables. The memory location of the passed variable and parameter is the same and therefore, any change to the parameter reflects in the variable as well.

.. code:: c++

   #include <iostream>
   using namespace std;
   void swap(int& x, int& y)
   {
       int z = x;
       x = y;
       y = z;
   }

   int main()
   {
       int a = 45, b = 35;
       cout << "Before Swap\n";
       cout << "a = " << a << " b = " << b << "\n";

       swap(a, b);

       cout << "After Swap with pass by reference\n";
       cout << "a = " << a << " b = " << b << "\n";
       return 0;
   }
   
  
Difference Between Reference Variable and Pointer Variable:    
#. A pointer can be re-assigned while a reference cannot, and must be assigned at initialization only.
#. Pointers can iterate over an array, we can use increment/decrement operators to go to the next/previous item that a pointer is pointing to.
#. A pointer is a variable that holds a memory address. A reference has the same memory address as the item it references.
#. A pointer to a class/struct uses ‘->’ (arrow operator) to access its members whereas a reference uses a ‘.’ (dot operator)
#. A pointer needs to be dereferenced with * to access the memory location it points to, whereas a reference can be used directly.
