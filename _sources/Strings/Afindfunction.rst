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

.. index:: traversal; eureka, eureka

A ``find`` Function
-------------------

Here is an implementation for a ``find`` function. It searches a string for the first occurrence of a character and returns its index. If the character is not found, the function returns ``-1``.
In a sense, ``find`` is the opposite of the indexing operator. Instead of taking an index and extracting the corresponding character, it takes a character and finds its location. 

.. activecode:: st09
    
    def find(astring, achar):
        """
        Find and return the index of achar in astring.  
        Return -1 if achar does not occur in astring.
        """
        ix = 0
        found = False
        while ix < len(astring) and not found:
            if astring[ix] == achar:
                found = True
            else:
                ix = ix + 1
        if found:
            return ix
        else:
            return -1
        
    print(find("Compsci", "C"))
    print(find("Compsci", "i"))
    print(find("Compsci", "p"))
    print(find("Compsci", "x"))
    


The ``while`` loop in this example uses a slightly more complex condition than we have seen in previous programs.  Here there are two parts to the condition.  We want to keep going if there
are more characters to look through and we want to keep going if we have not found what we are  looking for.  The variable ``found`` is a boolean variable that keeps track of whether we have found the character we are searching for.  It is initialized to *False*.  If we find the character, we reassign ``found`` to *True*.

The other part of the condition is the same as we used previously to traverse the characters of the string.  Since we have now combined these two parts with a logical ``and``, it is necessary for them both to be *True* to continue iterating.  If one part fails, the condition fails and the iteration stops.

When the iteration stops, we simply ask a question to find out why and then return the proper value.

.. note::

	This pattern of computation is sometimes called a eureka traversal because as
	soon as we find what we are looking for, we can cry Eureka!  and stop looking.  The way
	we stop looking is by setting ``found`` to True which causes the condition to fail.

Here is another version of the ``find`` function. It does not utilize the ``found`` variable. Instead, it immediately returns upon finding a match to ``aChar``.

.. activecode:: st10
    
    def find(astring, achar):
        """
        Find and return the index of achar in astring.  
        Return -1 if achar does not occur in astring.
        """
        ix = 0
        while ix < len(astring):
            if astring[ix] == achar:
                return ix  # eureka
    
            ix = ix + 1    # advance to the next index

        return -1 # no match found in astring
        
    print(find("Compsci", "C"))
    print(find("Compsci", "i"))
    print(find("Compsci", "p"))

    print(find("Compsci", "x"))

.. admonition:: Modify the program ...

   The ``find`` function works and it is important to understand this technique. However, one  of the string methods (section 9.13) gives us this same ability without our having to write a function.

   - On line 18, use a string **method** to find the index of ``p`` in ``Compsci``. This should produce the same result as line 17.

   - On line 20, use a string **method** to find the index of ``x`` in ``Compsci``. This should produce the same result as line 19.




