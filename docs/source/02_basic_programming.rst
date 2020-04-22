=================
Basic Programming
=================

This section of the curriculum will introduce the reader to the basics of
Object Oriented Programming, specifically through use of the language C++. By
the end of this section, you should be able to understand the building blocks
of a basic program and read the starter code that we provide.

What is programming?
====================

Let’s pretend that a computer is like a chef, and that a program is like a
recipe. However, unlike a normal chef, a computer has no intuition: it can’t
improvise, and it can’t respond to unexpected problems, unless solutions are
explicitly listed in the recipe. An example recipe might have sections that
repeat until a certain condition is met (a loop), conditional segments (if-else
statements), or have an error that makes the recipe fail (a bug). Even though
the chef has limitations, it’s still much easier to make 100 recipes if you can
give the recipe to 100 chefs and ask them each to make one, rather than having
one chef do all the work themselves. However, it requires the person writing
the recipe to have a very thorough understanding of the tasks being done and
where they could go wrong.

In this curriculum, the Arduino – a microcontroller with some sensors attached
– will act as our chef, and the code that will direct the Arduino will be the
recipe. To allow you to control the Arduino and the information it will
collect, you will need to understand how to write a recipe (write code!).
Below you will find subsections, first giving an example program, and then
the rest detailing the various types of “recipe steps” that you can use when
writing code.

An Example Program: Turning on the Lights
=========================================

As an example, we’re going to write some pseudocode (and eventually some real
code) as if we are an Arduino that allows a button to turn on a lightswitch. A
real world analogy would be like someone waiting by a lightswitch, waiting to
hear a bell. Once they hear the bell, they turn on the light switch.

Our recipe looks roughly like:

.. code-block:: txt

    1. Setup: stand up and move to the lightswitch, listen for the bell
    2. While the bell has not chimed:
         a. Listen for the bell
         b. If the bell chimes, exit this loop
    3. Flip the light switch

These instructions are relatively simple, and would be understandable by a
reasonable person. Unfortunately, a computer is not a reasonable person, and it
needs more detailed instructions. Therefore, we have to translate the
pseudocode into “actual” code. We’ll use the C++ syntax, which you will be able
to get a better sense for what you will actually be producing later.

.. code-block:: cpp

    void setup();
    void listenForBell();
    void switchLightSwitch();
    bool isBellGoingOff = false;
    int main() {
        setup();
        while(isBellGoingOff == false){
            listenForBell();
            if(isBellGoingOff == true){
                break;
            }
        }
        switchLightSwitch();
    }

If you aren’t familiar with C++, there will doubtlessly be several parts of the
code that don’t make sense at first glance. The first part (indicated in red)
is simply setup code, declaring functions and a variable that are used later
on. The function called “main()” is the main “recipe” that the computer would
follow. You can see that in that “recipe,” the first thing is calling the
“setup()” function, which tells the person to stand up and move to the light
switch and listen for the bell. Then the next step is the while loop, which
tells the person to listen until the bell goes off. Inside the loop, once the
person hears the bell going off, they break out of the loop and then switch the
light switch. Don’t worry if there are still some parts that don’t make sense
to you! By the end, you should be able to come back and understand what is
happening.  (Note:  The code above will not actually be able to run!  There are
a couple of things missing, it is there just for visual representation.)


Variables and Types
===================

In C++, data is stored in **variables**. Variables come in several different forms,
known as **types**. This type can range from a boolean value (i.e. only “true”
or “false”) to a string (a collection of letters) or a number. In order to use
a variable, you must first declare that variable (basically, you have to tell
the computer that it exists before you can use it). Here’s a list of several
common types along with how to declare them:

- ``int`` - An integer. Can hold any value from -2,147,483,648 to 2,147,483,647
  as long as it is a whole number.
  - ``int number = 1;``
- ``double`` - A number with a decimal point.
  - ``double number2 = 1.10;``
- ``char`` - A single letter or punctuation mark, which can be converted to and from an integer using ASCII values.
  - ``char letter = ‘h’;``
- ``vector`` - A flexible container that can hold collections of any type of variable.
  - ``vector<int> numbers = {1, 2, 3, 4};``
- ``string`` - A collection of characters that can form a word, a sentence, or more.
  - ``string word = “Hello!”;``
- ``bool`` - A true/false Boolean value.
  - ``bool isThisTrue = true;``

When declaring a variable, you can either assign it a value when you declare
it, or you can leave it blank until you need it. We recommend assigning it a
value at declaration, because it often can make debugging easier. Also note
from the above examples that most lines in C++ have to end with a semicolon.
This is so the computer can understand what the end of one “step” of the recipe
is.

If Statements
=============

Suppose you have decided to bake some cookies for yourself one evening, and are
trying to decide which kind of cookies to make. You think that chocolate chip
cookies sound great, but if you don’t have any chocolate chips, snickerdoodles
will be good too. You have to go check your pantry for ingredients, and then
you can decide which recipe to start making. This is basically what an
if-statement is: the computer checks to see what value it has, and then makes a
decision about what instructions to follow based on that value. The basic
structure of an if-statement looks like this:

.. code-block:: cpp

    if (condition) {
        // instructions to follow if condition is true
    }
    else if(condition2) {
        // instructions to follow if condition is false and condition2 is true
    }
    else {
        // instructions to follow if condition and condition2 are false
    }

You can use as many else-if-statements as you want, just bear in mind that ONLY
the first path with a true condition will be executed. If there is one
if-statement, three else-if-statements, and one else-statement and the
if-statement condition is true, then only the instructions inside the
if-statement will run, even if the conditions for one of the else-if-statements
is also true.  The else statement is only located at the end of the if and
else-if chain because it will catch any statements that do not meet any of the
previous if statements.  It cannot be located anywhere else except for the end
of an if and else-if chain.


Logical Expressions
===================

If you want to be able to use if-statements, you have to understand how to
write conditions! Conditions are created using logical expressions, which will
always evaluate to either true or false. For example, “2 is greater than x”
would be a logical expression, because it is always true or false, depending on
the value of x. How do we express that in C++ though? It’s more intuitive than
you might think. For this example, it would be “2 > x”. Here is a list of some
common logical operators, which you can use and combine to create conditional
statements:

- equal to: ``==``
- not equal to: ``!=``
- less than: ``<``
- greater than: ``>``
- less than or equal to: ``<=``
- greater than or equal to: ``>=``
- not: ``!``
- and: ``&&``
- or: ``||``

If you wanted to use an if-statement to check whether an integer variable
“number” was greater than or equal to 7, it might look like this:

.. code-block:: cpp

    if (number >= 7) {
        // do something here
    }

The “and” (``&&``) and “or” (``||``) operators are used to combine logical
expressions together.  For example, if we add to the code above another logical
expression like this:

.. code-block:: cpp

    if(number >= 7 && number < 10) {
        // do something here
    }

Then the thing inside of the if statement will only be run if both the number
is greater than or equal to seven AND the number is smaller than 10.  If the &&
operator was replaced with an || operator, then only one of the logical
expressions needs to be true in order for the statement inside of the if
statement to be run.

Also note from the above example that any text on a line after two backslashes
is ignored as a comment, and will not affect how the code runs (it will,
however, make it easier for the next person who sees your code to understand
how it works!).


Operators
=========

There are many types of operators that are used in C++. Many of them are
familiar from arithmetic (i.e. addition, subtraction), but some will probably
be unfamiliar and need some explaining. Here’s a list of common operators that
will be useful in many programs:


- ``+``, simple addition or concatenation
    - Concatenation takes two things (usually strings or chars) and combines them into one string.
- ``-``, simple subtraction
- ``/``, simple division. Keep in mind that dividing integers will give you an integer rounded to the nearest whole number, whereas dividing doubles will give you precise decimal division
- ``*``, multiplication
- ``++``, increment operator. This will add one to an integer.
    - Example: if x = 1 and the next line says “++x” or “x++”, then the value of x will be 2 after that line.
- ``--``, decrement operator. Works the same as the increment operator, but subtracts one instead of adding one.
- ``%``, modulus division. This is useful in limited applications, but will likely not be necessary for the purposes of this tutorial.


Loops
=====

There are several different kinds of loops that we use in C++ to accomplish
tasks. Imagine that you are a chef making banana bread, and the instructions
tell you to stir until smooth. How would you translate that into code? We can’t
just write “stir until smooth” because our very literal minded chef wouldn’t
understand. Instead, we can use a loop! The two most common types of loops are
while loops and for loops. A while loop iterates through a set of instructions
until the provided condition becomes false. A while loop usually looks like
this:

.. code-block:: cpp

    while(condition == true) {
        // do something
    }

So, for our example, the code might look something like this:

.. code-block:: cpp

    while(smooth == false) {
        stir();
    }

A very important concept for while loops is the idea of “infinite loops”, which
means that the while loop will run without end.  This happens when the
condition in the while loop keeps evaluating to true.  To avoid this, there
must be something within the while loop that will cause the condition to
eventually evaluate to false.

The biggest difference between a while loop and a for loop is that a while loop
goes until the condition is false, a for loop goes a predetermined number of
steps and then stops. This would be useful if a recipe said “stir 75 times”
because who wants to write 75 lines of “stir” over and over again? Instead, we
could just write something like the for loop below:

.. code-block:: cpp

    for(int i = 0; i < 75; ++i){
        stir();
    }

This may look a lot more overwhelming than the while loop (what is the ++ for?
Why are there three parts? What do they mean?), it’s actually not too bad. The
first part (int i = 0) is where you create some type of counter variable - this
doesn’t have to be an integer, but it’s customary to be an integer and start at
zero. You can call it “i”, but if it helps you keep your variables straight,
name it whatever you want! The second part tells you when the loop should stop:
in this case, it says to stop when the counter variable is 75 or greater
because we want exactly 75 stirs!

Finally, the last part tells the counter variable how it should change after
every iteration. In this case, since we’re just counting to 75, we tell it to
add one every time using the ++ operator (see the “Operators” section for
more).


Functions
=========


Functions are a key element of programming in any language, and C++ is no
exception. Imagine if you had to write out every single step for a 100 step
recipe, but 75 of the steps were the same series of three steps over and over
again. Wouldn’t that be tedious (and prone to errors)? What if you could just
say “do steps 13-15” instead? That’s basically what a function does: simplifies
a set of instructions that need to be done multiple times to shorten code and
make it more readable. In C++, functions are traditionally defined above the
“main” function, and look like this:

.. code-block:: cpp

    returnVariableType functionName(inputVariableType inputVariableName) {
        // do something
        return returnVariable;
    }

For example, a function to multiply two numbers together and return the result
might look like this in C++:

.. code-block:: cpp

    int multiplyNumbers(int inputA, int inputB) {
        int multiplicationResult = inputA * inputB;
        return multiplicationResult;
    }

Then, to call that function from somewhere else in the code, you can simply
write ``multiplyNumbers(x, y);``.
