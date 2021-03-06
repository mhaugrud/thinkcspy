..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: strings-15-
   :start: 1

.. index:: operator; in, in, substring, string; substring

The ``in`` and ``not in`` operators
-----------------------------------

The ``in`` operator tests if one string is a substring of another:

.. activecode:: sto
    
    print('p' in 'apple')
    print('i' in 'apple')
    print('ap' in 'apple')
    print('AP' in 'apple')

Note that a string is a substring of itself, and the empty string is a substring of any other string. (Also note that computer scientists like to think about these **boundary cases** quite carefully!) 

.. activecode:: stp
    
    print('a' in 'a')
    print('apple' in 'apple')
    print('' in 'a')
    print('' in 'apple')
    
The ``not in`` operator returns the logical opposite result of ``in``.

.. activecode:: stq

    print('x' not in 'apple')


.. admonition:: Modify the program ...

   Change ``x`` to some letter that **is** in ``apple``.

