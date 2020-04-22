========================
C++ Syntax and Semantics
========================

Although many details and rules about C++ don’t fit into any category neatly,
they are very important to understanding how a C++ program works, and how to
write a new one. This section will contain a wide variety of these smaller
details and rules, along with a brief blurb about the importance of each one.

Variable Names
==============

Each variable must have a name, and they must all be distinct – if there are
two variables called “number”, how will the computer know which one you mean?
Names must start with a character (not a number), and can’t be a reserved word
(aka a word that has an important meaning in C++).  For example, a variable
can’t be named ``int`` because that’s already a word in C++ that we use to make
variables.

Scope
=====
The “scope” of a variable is where it exists in the program - the variable
might exist in a particular function or be global (exist everywhere in the
program)

The programmer controls the scope of variables - a variable exists in between a
set of curly brackets ({ }).

If this doesn’t make sense, take a second to scroll back to a previous example
code section. Look at where the curly brackets appear - they hold a section of
code that is intended to execute together. For example, a function uses a set
of curly brackets to contain all of the code belonging to that function. A
variable inside those curly brackets exists only in that function - it is a
local variable..

A variable declared outside of a function is a global variable - it will exist
everywhere after that line in the program, regardless of curly brackets.

You can never have two variables with the same name in the same scope. This
rule has many implications:

No local variables can have the same name as a global variable, since global
variables exist in all scopes.

There can never be two variables with the same name in a single function or
if-statement or loop.


Pass by value
=============

When you call a function normally and pass in a variable, you are passing by
value - the computer takes whatever you are passing in, and makes a copy of it
so that any transformations done by the function aren’t permanent and don’t
affect the variable in its original scope.

Example: if you have variables ``x`` and ``y`` that are integers, and you pass
them into the function ``multiplyNumbers`` that we used as an example earlier,
it would look like this: ``multiplyNumbers(x,y);``. The computer makes a copy
of ``x`` and ``y``, and then those copies are used to compute the product of
``x`` and ``y``. If ``x`` or ``y`` was changed during the function, the
originals would still have their starting value.

Pass by reference
=================
What happens when you want the changes from a function to last? Or what happens
if the variable you want to pass into a function is HUGE, and making a copy of
it would be very slow? That’s when you should pass by reference, or send the
original value into the function to get modified.

You can pass by reference by changing the function definition! Let’s take a
look at the multiplyNumbers function header as an example:

.. code-block:: cpp

    int multiplyNumbers(int inputA, int inputB)

This is the pass by value version.

.. code-block:: cpp

    int multiplyNumbers(int &inputA, int &inputB)

This is the pass by reference version.

By simply adding an ampersand (``&``) between the type and the name of a
variable in the function, you can make that variable pass by reference.

Structs
=======
A struct is a group of variables that a programmer can lump together to keep related information accessible. It’s basically a type that you, the programmer, gets to control.
For example, you could have a struct called “dog” which could have variables like “height”, “weight”, and “breed”.
To define a struct, use the following format (make sure that the definition goes in the global scope!):

.. code-block:: cpp

    struct dog {
        int height;
        int weight;
        string breed;
    };

Arrays
======

An array is like a simpler version of a vector - it has fewer features and has
more restrictions, but the basic idea is the same: storing values of the same
type in a certain order.

You must know exactly what size array you are going to use before you can
declare the array. Unlike a vector, it cannot be resized later.

You most likely won’t need to use an array in C++, but they are fairly common
in C

In C, a string is just an array of chars.

Definitions vs. declarations
============================

You may have noticed throughout this document that we used the words definition
and declaration at different places when talking about creating variables and
functions. It is a key distinction that will save you from many errors down the
road.

A definition defines what something is: when you create a new type of struct or
write a new function, those are definitions.

A declaration is just saying that something exists. You declare a variable when
you say ``int x;``.

Oftentimes, declaration and definition are done in the same step. For example,
``int x = 1;`` is both a declaration and a definition, because you are saying
to the computer that the variable x exists, AND that it has the value of 1.

This is true for functions as well! You can just declare a function by only
including a header and then define it somewhere else. This is not always
necessary, but sometimes makes it easier to read long and complex code.


Header files and libraries
==========================

What if you need a function for a difficult task that you don’t want to write
yourself? For example, reading and writing to a CSV file would be difficult and
annoying functions to write yourself.

Fortunately, there are lots of functions out there that have already been
written by very smart people and that you can use!

Google the function that you need and it will almost certainly exist in a
library written by someone else. To include that function in your code, just
look for the library name, and include it at the top of the relevant file.

For example, let’s say that you need the square root function (named ``sqrt()``).
This is within the cmath library, and can be included by placing the line
``#include <cmath>`` at the top of the file.

You can also link other files to this file so that they share variables and
other key aspects. This is good for increasing readability by sectioning off
big chunks of code into smaller pieces, and is done via including.

Simply add the line ``#include fileName.fileExtension`` at the top of the file.

StackOverflow and Questions
===========================
No matter how comprehensive a guide is, it’s simply not possible to anticipate
every question and error that you might have. Fortunately, there are millions
of programmers in the world, and they all also have questions! 99.99% of the
time, someone has already had the same question that you have, and the answer
can be found somewhere on Stack Overflow or a similar website. It might take
some digging, but it’s almost certainly there. Additionally, there are sites
like CPP Reference that allow you to consult documentation for C++ so that you
can see exactly how existing functions and types work if you have questions
about those.
