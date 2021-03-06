..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-11-
   :start: 1

.. index:: update, increment, decrement, initialize

Updating Variables
------------------

One of the most common forms of reassignment is an **update** where the new value of the variable depends on the old.  

.. youtube:: Px1c-3GP-5o
    :divid: updatevid
    :height: 315
    :width: 560
    :align: left

|

For example,

.. sourcecode:: python

    x = x + 1

This means get the current value of x, add one, and then update x with the new value.  The new value of x is the old value of x plus 1.  Although this assignment statement may look a bit strange, remember that executing assignment is a two-step process.  First, evaluate the right-hand side expression.  Second, let the variable name on the left-hand side refer to this new resulting object.  The fact that ``x`` appears on both sides does not matter.  The semantics of the assignment statement makes sure that there is no confusion as to the result. The visualizer makes this very clear.

.. showeval:: se_updatevar1
   :trace_mode: true

   x = 6
   x = x + 1
   ~~~~
   x = 6
   x = {{x}}{{6}} + 1
   x = {{6 + 1}}{{7}}


..    x = 6 + {{1}}{{1}}


.. activecode:: sdz

    #x = 6        # initialize x
    x = x + 1    # increment x
    print(x)
    x + 1 = x    # ERROR

.. admonition:: Fix the error ...

   - In an assignment statement the only thing that can be left of the ``=`` is a variable name. Delete line 4. Run.
   - You must **initialize** a variable before you can update it. Remove ``#`` at the beginning of line 1. Run.
   - Copy lines 2 and 3 to lines 4 and 5
   - On line 4, change ``+`` to ``-`` and ``increment`` to ``decrement``



If you try to update a variable that doesn't exist, you get an error because Python evaluates the expression on the right side of the assignment operator before it assigns the resulting value to the name on the left. Before you can update a variable, you have to **initialize** it, usually with a simple assignment.  In the above example, ``x`` was initialized to 6.

Updating a variable by adding 1 is called an **increment** and subtracting 1 is called a **decrement**.



**Check your understanding**

.. mchoice:: mc2m
   :answer_a: 12
   :answer_b: -1
   :answer_c: 11
   :answer_d: Nothing.  An error occurs because x can never be equal to x - 1.
   :correct: c
   :feedback_a: The value of x changes in the second statement.
   :feedback_b: In the second statement, substitute the current value of x before subtracting 1.
   :feedback_c: Yes, this statement sets the value of x equal to the current value minus 1.
   :feedback_d: Remember that variables in Python are different from variables in math in that they (temporarily) hold values, but can be reassigned.


   What is printed when the following statements execute?

   .. code-block:: python

     x = 12
     x = x - 1
     print(x)

.. mchoice:: mc2n
   :answer_a: 12
   :answer_b: 9
   :answer_c: 15
   :answer_d: Nothing.  An error occurs because x cannot be used that many times in assignment statements.
   :correct: c
   :feedback_a: The value of x changes in the second statement.
   :feedback_b: Each statement changes the value of x, so 9 is not the final result.
   :feedback_c: Yes, starting with 12, subtract 3, than add 5, and finally add 1.
   :feedback_d: Remember that variables in Python are different from variables in math in that they (temporarily) hold values, but can be reassigned.


   What is printed when the following statements execute?

   .. code-block:: python

     x = 12
     x = x - 3
     x = x + 5
     x = x + 1
     print(x)

.. parsonsprob:: question2_10_3

   Construct the code that will result in the value 134 being printed.
   -----
   mybankbalance = 100
   mybankbalance = mybankbalance + 34
   print(mybankbalance)


.. note::

   This workspace is provided for your convenience.  You can use this activecode window to try out anything you like.

   .. activecode:: sd0



