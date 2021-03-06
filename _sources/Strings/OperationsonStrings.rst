..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: strings-3-
   :start: 1

.. index:: concatenation, overloading, string; concatenation

Operations on Strings
---------------------

In general, you cannot perform mathematical operations on strings, even if the
strings look like numbers. The following are illegal (assuming that ``message``
has type string):

.. sourcecode:: python
    
    message - 1   
    "Hello" / 123   
    message * "Hello"   
    "15" + 2

Interestingly, the ``+`` operator does work with strings, but for strings, the
``+`` operator represents **concatenation**, not addition.  Concatenation means
joining the two operands by linking them end-to-end. For example:

.. activecode:: sta
    :nocanvas:

    fruit = "banana"
    bakedGood = "nut bread"

    print(fruit + bakedGood)

The output of this program is ``banananut bread``. The two strings are run together. Sometimes this is what we want but other times we would like to separate them with a space (or some other character).

.. admonition:: Modify the program ...

   - On line 3, declare another string that is just a space character.

   - Edit line 4, to concatenate the three strings to produce the output ``banana nut bread``. 

The ``*`` operator also works on strings.  It performs repetition. For example, ``'Fun'*3`` is ``'FunFunFun'``. One of the operands has to be a string and the other has to be an integer.

.. activecode:: stb
    :nocanvas:

    print("Go" * 6)

    name = "Dragons"
    print(name * 3)

    print(name + "Go" * 3)

    print((name + "Go") * 3)

This interpretation of ``+`` and ``*`` makes sense by analogy with addition and multiplication. Just as ``4*3`` is equivalent to ``4+4+4``, we expect ``"Go"*3`` to be the same as ``"Go"+"Go"+"Go"``, and it is.  Note also in the last
example that the order of operations for ``*`` and ``+`` is the same as it was for arithmetic. The repetition is done before the concatenation.  If you want to cause the concatenation to be
done first, you will need to use parenthesis.

.. note::
   The extension of familiar operations to different data types is called **overloading**. Overloading should be defined in a manner that makes sense, both with the usual use of the operation and with the new data type.

**Check your understanding**

.. mchoice:: mc8a
   :answer_a: python rocks
   :answer_b: python
   :answer_c: pythonrocks
   :answer_d: Error, you cannot add two strings together.
   :correct: c
   :feedback_a: Concatenation does not automatically add a space.
   :feedback_b: The expression s+t is evaluated first, then the resulting string is printed.
   :feedback_c: Yes, the two strings are glued end to end.
   :feedback_d: The + operator has different meanings depending on the operands, in this case, two strings.


   What is printed by the following statements?
   
   .. code-block:: python

      s = "python"
      t = "rocks"
      print(s + t)



.. mchoice:: mc8b
   :answer_a: python!!!
   :answer_b: python!python!python!
   :answer_c: pythonpythonpython!
   :answer_d: Error, you cannot perform concatenation and repetition at the same time.
   :correct: a
   :feedback_a: Yes, repetition has precedence over concatenation
   :feedback_b: Repetition is done first.
   :feedback_c: The repetition operator is working on the excl variable.
   :feedback_d: The + and * operator are defined for strings as well as numbers.


   What is printed by the following statements?
   
   .. code-block:: python
 
      s = "python"
      excl = "!"
      print(s+excl*3)




