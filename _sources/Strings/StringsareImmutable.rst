..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: strings-9-
   :start: 1

.. index:: mutable, immutable

Strings Are Immutable
---------------------

One final thing that makes strings different from some other Python collection types is that
you are not allowed to modify the individual characters in the collection.  It is tempting to use the ``[]`` operator on the left side of an assignment,
with the intention of changing a character in a string.  For example, in the following code, we would like to change the first letter of ``greeting``.

.. activecode:: stj
    
    greeting = "Hello, world!"
    greeting[0] = 'J'            # ERROR!
    print(greeting)

Instead of producing the output ``Jello, world!``, this code produces the
runtime error ``TypeError: 'str' object does not support item assignment``.

Strings are **immutable**, which means you cannot change an existing string. The
best you can do is create a new string that is a variation on the original.

.. activecode:: stk
    
    greeting = "Hello, world!"
    newGreeting = 'J' + greeting[1:]
    print(newGreeting)
    print(greeting)            # same as it was

The solution here is to concatenate a new first letter onto a slice of
``greeting``. This operation has no effect on the original string.

.. admonition:: Modify the code ...

   - In line 2, change ``newGreeting`` to ``greeting``

   - Comment out line 3

   - Run and notice ``greeting`` is no longer the same as it was


**Check your understanding**

.. mchoice:: mc8i
   :answer_a: Ball
   :answer_b: Call
   :answer_c: Error
   :correct: c
   :feedback_a: Assignment is not allowed with strings.
   :feedback_b: Assignment is not allowed with strings.
   :feedback_c: Yes, strings are immutable.

   What is printed by the following statements:
   
   .. code-block:: python

      s = "Ball"
      s[0] = "C"
      print(s)


