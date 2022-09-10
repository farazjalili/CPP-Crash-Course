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

     return 0;
   }
   
