..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-2-
   :start: 1

.. index:: value, data type, string, integer, int, float, class, triple quoted string, type, str

Values and Data Types
---------------------

A **value** is one of the fundamental things --- like a word or a number --- that a program manipulates. The values we have seen so far are ``5`` (the result when we added ``2 + 3``), and ``"Hello, World!"``.  We often refer to these values as **objects** and we will use the words value and object interchangeably.

.. note::
	Actually, the 2 and the 3 that are part of the addition above are values(objects) as well.

These objects are classified into different **classes**, or **data types**: ``4`` is an *integer*, and ``"Hello, World!"`` is a *string*, so-called because it contains a string or sequence of letters. You (and the interpreter) can identify strings because they are enclosed in quotation marks.

If you are not sure what class a value falls into, Python has a function called **type** which can tell you.

.. activecode:: sda
    :nocanvas:

    print(type("Hello, World!"))
    print(type(17))
    print("Hello, World")

Not surprisingly, strings belong to the class **str** and integers belong to the class **int**.

.. note::

	When we show the value of a string using the ``print`` function, such as in the third example above, the quotes are not present in the output.  The value of the string is the sequence of characters inside the quotes.  The quotes are only necessary to help Python know what the value is.


In the Python shell, it is not necessary to use the ``print`` function to see the values shown above.  The shell evaluates the Python function and automatically prints the result.  For example, consider the shell session shown below.  When
we ask the shell to evaluate ``type("Hello, World!")``, it responds with the appropriate answer and then goes on to
display the prompt for the next use.

::

	Python 3.1.2 (r312:79360M, Mar 24 2010, 01:33:18)
	[GCC 4.0.1 (Apple Inc. build 5493)] on darwin
	Type "help", "copyright", "credits" or "license" for more information.
	>>> type("Hello, World!")
	<class 'str'>
	>>> type(17)
	<class 'int'>
	>>> "Hello, World"
	'Hello, World'
	>>>

Note that in the last example, we simply ask the shell to evaluate the string "Hello, World".  The result is as you might expect, the string itself.

Continuing with our discussion of data types, numbers with a decimal point belong to a class called **float**, because these numbers are represented in a format called *floating-point*.  At this stage, you can treat the words *class* and *type*
interchangeably.  We'll come back to a deeper understanding of what a class is in later chapters.

.. activecode:: sdb
    :nocanvas:

    print(3)
    print(3.0)
    print(3.2)
    print(1.2345e2)

    print(type(3))
    print(type(3.0))
    print(type(3.2))
    print(type(1.2345e2))
    #


.. admonition:: Modify the program ...

   On line 10 of the above activecode, type a comment that explains what ``e2`` (in lines 4 and 9) means. Run.

What about values like ``"3"`` and ``"3.2"``? They look like numbers, but they are in quotation marks like strings.

.. activecode:: sdc
    :nocanvas:

    print(type("3"))
    print(type("3.2"))

They're strings!

Strings in Python can be enclosed in either single quotes (``'``) or double 
quotes (``"``), or three of the same quote character (``'''`` or ``"""``)

.. activecode:: sdd
    :nocanvas:

    print('This is a string.')
    print("And so is this.")
    print("""and this.""")
    print('''and even this...''')
    print(type('This is a string.') )
    print(type("And so is this.") )
    print(type("""and this.""") )
    print(type('''and even this...''') )


Double quoted strings can contain single quotes inside them, as in ``"Bruce's beard"``, and single quoted strings can have double quotes inside them, as in ``'The knights who say "Ni!"'``.

What do you think would happen if the string already contained quotes both single and double?


.. activecode:: sde
    :nocanvas:

    print("Oh no", she exclaimed, "Ben's bike is broken!")


.. admonition:: Fix the error ...

   When you run the above activecode a syntax error occurs. Type triple quotes ``'''`` at the beginning and end of the string. Then it will run with no errors.

Strings enclosed with three occurrences of either quote symbol are called triple quoted strings.  They can contain either single or double quotes

Triple quoted strings can even span multiple lines:

.. activecode:: sdf
    :nocanvas:

    print('This message

    spans several
    lines.')


.. admonition:: Fix the error ...

   When you run the above activecode a syntax error occurs. Change the quotes ``'`` to triple quotes, either ``'''`` or ``"""``. Then it will run with no errors.

Python doesn't care whether you use single or double quotes or the three-of-a-kind quotes to surround your strings.  Once it has parsed the text of your program or command, the way it stores the value is identical in all cases, and the surrounding quotes are not part of the value.

.. note::
   Python programers usually choose to surround their strings by single quotes.

When you type a large number, you might be tempted to use commas between groups of three digits, as in ``42,000.1``. This is not a legal number in Python, but it does mean something else, which is legal:

.. activecode:: sdg
    :nocanvas:

    print(42000.1)
    print(42,000.1)


Well, that's not what we expected at all! Because of the comma, Python treats this as a *pair* of values.     In fact, the print function can print any number of values as long as you separate them by commas.  Notice that the values are separated by spaces when they are displayed.

.. activecode:: sdh
    :nocanvas:

    print(42, 17, 56, 34, 11, 4.35, 32)
    print(3.4, "hello", 45)

Remember not to put commas or spaces in your integers, no
matter how big they are. Also revisit what we said in the previous chapter: formal languages are strict, the notation is concise, and even the smallest change might mean something quite different from what you intended.

**Check your understanding**

.. mchoice:: mc2a
   :answer_a: Print out the value and determine the data type based on the value printed.
   :answer_b: Use the type function.
   :answer_c: Use it in a known equation and print the result.
   :answer_d: Look at the declaration of the variable.
   :correct: b
   :feedback_a: You may be able to determine the data type based on the printed value, but it may also be  deceptive, like when a string prints, there are no quotes around it.
   :feedback_b: The type function will tell you the class the value belongs to.
   :feedback_c: Only numeric values can be used in equations.
   :feedback_d: In Python variables are not declared.

   How can you determine the type of a variable?

.. mchoice:: mc2b
   :answer_a: Character
   :answer_b: Integer
   :answer_c: Float
   :answer_d: String
   :correct: d
   :feedback_a: It is not a single character.
   :feedback_b: The data is not numeric.
   :feedback_c: The value is not numeric with a decimal point.
   :feedback_d: Strings can be enclosed in single quotes.

   What is the data type of 'this is what kind of data'?



