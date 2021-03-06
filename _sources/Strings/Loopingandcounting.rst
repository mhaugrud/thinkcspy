..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: strings-14-
   :start: 1

Looping and Counting
--------------------

Here is another variation on the theme of iterating through the characters of a string.


The following program counts the number of times a particular letter, ``aChar``, appears in a
string.  It is another example of the accumulator pattern that we have seen in previous chapters.

.. activecode:: stt

    def count(text, aChar): 
        lettercount = 0
        for c in text:
            if c == aChar:
                lettercount = lettercount + 1
        return lettercount

    print(count("banana","a"))    
    print(count("banana","b"))    

The function ``count`` takes a string as its parameter.  The ``for`` statement iterates through each character in
the string and checks to see if the character is equal to the value of ``aChar``.  If so, the counting variable, ``lettercount``, is incremented by one.
When all characters have been processed, the ``lettercount`` is returned.

.. admonition:: Modify the program ...

   In line 9, change ``"b"`` to ``"B"``.

.. note::
   As we will later see, this function (and other similar ones) is implemented as a method of the string class.
