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
   
   
The C++ getline() is a standard library function that is used to read a string or a line from an input stream. It is a part of the ``<string>`` header. The getline() function extracts characters from the input stream and appends it to the string object until the delimiting character is encountered.

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
