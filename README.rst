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

   int main (int argc, char **argv)
   {
       int i;
       std::cout << "Please enter an integer value: ";
       std::cin >> i;
       std::cout << "The value you entered is " << i  << std::endl;
       return 0;
   }
