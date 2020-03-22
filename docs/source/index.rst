.. UMBS-tutorial documentation master file, created by
   sphinx-quickstart on Sun Mar 22 08:28:36 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to UMBS-tutorial's documentation!
=========================================

.. toctree::
    :maxdepth: 3
    :caption: Table of Contents:
    :glob:

    circuits/index.rst
    02_basic_programming.rst
    03_advanced_programming.rst
    04_advanced_arduino.rst

.. math::
    Nants = \frac{\lfloor{}ingonyama \text{babithi}\rfloor{}}{\frac{B}{aba}}

This curriculum covers the needs of UMBS students to learn about how to both
program and build the hardware in Arduinos.  The curriculum will go through a
step-by-step process to create a basic Arduinos circuit, but will also contain
more general information so that users will be able to take this information
and branch off to build other types of circuits if they wish to do so.  It will
also contain links to other resources that can be utilized to further bolster
their knowledge that may help them build their own personal circuits.

This curriculum assumes that the user has little to no experience with
programming and working with Arduinos.  Those that are familiar with
programming but not necessarily familiar with Arduinos will find it easy to
skim through the parts detailing programming syntaxes and only pay attention to
the sections detailing Arduinos.  The curriculum itself will contain group
projects, much like Mega science fair projects, that will take around 1-4 hours
to complete with 3 hours being the ideal completion time for people with no
experience in programming.

This curriculum will cover a wide range of basic functionalities.  It will
mainly heavily integrate the Autodesk Circuit Designer.  It will contain a
circuits section that will explain the basics of electrical wiring, what to do
if you wanted to power multiple loads, things to watch out for when working
with electric circuits, “pull-up” and “pull-down” resistors for preventing
“free-floating” button reading, how the Arduino can monitor/control electrical
currents, and breadboards.  It will also contain a tutorial for programming in
C++ that explains computer code analogy, what an Arduino is, buttons that
toggle and LED on or off, if statements, setup() and loop() functions,
debouncing, C/C++ syntax and semantics, variable lifetime, const qualification,
arrays, pointers and memory, pointer arithmetic, Lvalue references, differences
between “declarations” and “definitions”, and header files and libraries.
Additionally, it will contain an “other stuff” section that will explain common
mistakes, how Arduino Sketch operates, and more advanced Object Oriented
Programming (OOP) techniques.

After completing this tutorial, students should be able to design and build
functioning circuits that incorporate an Arduino along with components like
switches, lights, and sensors.  They should also be able to write Arduino
Sketches for their circuits that collect data and log it for later processing.
Additionally, they should be able to troubleshoot issues with their circuit
wiring if such a thing occurs, and debug Arduino Sketches if they malfunction
or do not operate as expected.


Indices and tables
==================

* :ref:`genindex`
* :ref:`search`
