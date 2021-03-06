..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: list-29-
   :start: 1

.. index:: iterable

Iterable Functions
------------------

We have seen how we can iterate over the elements of the various Python collections such as strings, 
lists, and tuples. For that reason, a collection like this is called an **iterable**.

The simplest way to iterate over such a collection is to use a ``for`` loop and iterate by item. However, 
there are circumstances where we need the index, even though iterating by index is more complicated. 

.. index:: enumerate

``enumerate``
^^^^^^^^^^^^^

The ``enumerate`` function gives us a way to iterate by item but still have access to the index. 
``enumerate`` constructs an ``(index, value)`` tuple for each item in the collection. We can then 
iterate over this collection of tuples by item.

.. activecode:: tdh1

   actress = ("Julia", "Roberts", 1967, "Pretty Woman", 1990, "Atlanta", "Georgia")
   for tup in enumerate(actress): # entire tuple
       print(tup)

   for (index, ch) in enumerate("Crunchy Frog"): # unpack tuple
       print(index, ch)

   fruit = ["apple", "orange", "banana", "cherry"]
   for (i, f) in enumerate(fruit):
       fruit[i] = f.upper()

   print(fruit)

.. note::
   Notice the different types of iterables in the previous examples: a tuple, a string, and a list.

.. index:: zip
       
``zip``
^^^^^^^

We may have a number of iterables, all with the same number of elements, that we want to match up, 
one with another.

The ``zip`` function enables us to create a collection of tuples with this one-to-one association.

.. activecode:: tdh2

   title = ["Duplicity", "Notting Hill", "Pretty Woman", "Erin Brockovich", "Eat Pray Love", "Mona Lisa Smile"]
   year = (2009, 1999, 1990, 2000, 2010, 2003)

   for movie in zip(title, year):
       print(movie)


.. admonition:: Modify the program ...

   Change ``movie`` in lines 4 and 5, to unpack the tuple (like what was done in the activecode at the
   top of the page, lines 5 and 6).

.. note::
   Both ``enumerate`` and ``zip`` take iterables as argument(s) and return an iterable.


