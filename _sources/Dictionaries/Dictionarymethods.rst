..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dict-3-
   :start: 1

.. index:: dictionary; method

Dictionary Methods
------------------

Dictionaries have a number of useful built-in methods.
The following table provides a summary and more details can be found in the 
`Python Documentation <http://docs.python.org/py3k/library/stdtypes.html#mapping-types-dict>`_.

==========  ==============      =======================================================
Method      Parameters          Description
==========  ==============      =======================================================
keys        none                Returns a view of the keys in the dictionary
values      none                Returns a view of the values in the dictionary
items       none                Returns a view of the key-value pairs in the dictionary
get         key                 Returns the value associated with key; None otherwise
get         key,alt             Returns the value associated with key; alt otherwise
==========  ==============      =======================================================

The ``keys`` method returns what Python 3 calls a **view** of its underlying keys.  
We can iterate over the view or turn the view into a 
list by using the ``list`` constructor function.

.. activecode:: tdj
    
    inventory = {'bananas': 312, 'pears': 525, 'oranges': 217, 'apples': 430}
  
    for akey in inventory.keys():     # the order in which we get the keys is not defined
        print("Got key", akey, "which maps to value", inventory[akey])     
       
    theKeys = list(inventory.keys())

    print(theKeys)


.. admonition:: Extend the program ...

   - Run the above activecode and notice the order of the keys when they are printed in line 8.

   - In line 7, sort the list ``theKeys``. Run and notice the order of the keys.

   - In line 9, write a for-loop that iterates by item over the list ``theKeys``.

   - In line 10 (the body of the loop), print the current key and the value in ``inventory`` for the current key. Run and notice the order.


It is so common to iterate over the keys in a dictionary that you can omit the ``keys`` method call in the ``for`` loop --- iterating over a dictionary implicitly iterates over its keys.

.. activecode:: tdk
    
    inventory = {'bananas': 312, 'pears': 525, 'oranges': 217, 'apples': 430}
  
    
    for k in inventory:     
        print("Got key", k)

 
As we saw earlier with strings and lists, dictionary methods use dot notation, which specifies the name of the method to the right of the dot and the name of the object on which to apply the method immediately to the left of the dot. The empty parentheses in the case of ``keys`` indicate that this method takes no parameters.

The ``values`` and ``items`` methods are similar to ``keys``. They return  view objects which can be turned into lists or iterated over directly.  Note that the items are shown as tuples containing the key and the associated value.

.. activecode:: tdl
    
    inventory = {'bananas': 312, 'pears': 525, 'oranges': 217, 'apples': 430}  
    
    print(list(inventory.values()))
    print(list(inventory.items()))

    for k in inventory:
        print("Got", k, "that maps to", inventory[k])
    
    for (k,v) in inventory.items():
        print(k, "maps to", v)

Note that tuples are often useful for getting both the key and the value at the same time while you are looping.  The two loops do the same thing.

    
The ``in`` and ``not in`` operators can test if a key is in the dictionary:

.. activecode:: tdm
    
    inventory = {'bananas': 312, 'pears': 525, 'oranges': 217, 'apples': 430}

    print('apples' in inventory)
    print('cherries' in inventory)

    if 'bananas' in inventory:
        print(inventory['bananas'])
    else:
        print("We have no bananas")
     

This operator can be very useful since looking up a non-existent key in a dictionary causes a runtime error.

The ``get`` method allows us to access the value associated with a key, similar to the ``[ ]`` operator.
The important difference is that ``get`` will not cause a runtime error if the key is not present.  It
will instead return None.  There exists a variation of ``get`` that allows a second parameter that serves as an alternative return value
in the case where the key is not present.  This can be seen in the final example below.  In this case, since "cherries" is not a key, return 0 (instead of None).

.. activecode:: tdn
    
    inventory = {'bananas': 312, 'pears': 525, 'oranges': 217, 'apples': 430}
    
    print(inventory.get("apples"))
    print(inventory.get("cherries"))

    print(inventory.get("cherries", 0))




.. note::

    This workspace is provided for your convenience.  You can use this activecode window to try out anything you like.

    .. activecode:: tdo


**Check your understanding**

.. mchoice:: mc11d
   :answer_a: cat
   :answer_b: dog
   :answer_c: elephant
   :answer_d: bear
   :correct: c
   :feedback_a: keylist is a list of all the keys which is then sorted.  cat would be at index 1.
   :feedback_b: keylist is a list of all the keys which is then sorted.  dog would be at index 2.
   :feedback_c: Yes, the list of keys is sorted and the item at index 3 is printed.
   :feedback_d: keylist is a list of all the keys which is then sorted.  bear would be at index 0.
   
   
   What is printed by the following statements?
   
   .. sourcecode:: python

     mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
     keylist = list(mydict.keys())
     keylist.sort()
     print(keylist[3])
   

.. admonition:: Modify the program ...

   .. activecode:: tdp
    
      inventory = {'bananas': 312, 'oranges': 525, 'pears': 217, 'apples': 430}
      
      
      for akey in inventory.keys():     
          print("key:", akey, "value:", inventory[akey])     
   
   - On lines 2 and 3, type instructions to make a list of sorted keys (similar to the above multiple choice question).

   - Edit line 4 to iterate over the sorted list
   

.. mchoice:: mc11e
   :answer_a: 2
   :answer_b: 0.5
   :answer_c: bear
   :answer_d: Error, divide is not a valid operation on dictionaries.
   :correct: a
   :feedback_a: get returns the value associated with a given key so this divides 12 by 6.
   :feedback_b: 12 is divided by 6, not the other way around.
   :feedback_c: Take another look at the example for get above.  get returns the value associated with a given key.
   :feedback_d: The integer division operator is being used on the values returned from the get method, not on the dictionary.
   
   
   What is printed by the following statements?
   
   .. sourcecode:: python

     mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
     answer = mydict.get("cat") // mydict.get("dog")
     print(answer)

   
   
.. mchoice:: mc11f
   :answer_a: True
   :answer_b: False
   :correct: a
   :feedback_a: Yes, dog is a key in the dictionary.
   :feedback_b: The in operator returns True if a key is in the dictionary, False otherwise.
   
   What is printed by the following statements?
   
   .. sourcecode:: python

     mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
     print("dog" in mydict)



.. mchoice:: mc11g
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: 23 is a value in the dictionary, not a key.  
   :feedback_b: Yes, the in operator returns True if a key is in the dictionary, False otherwise.
   
   What is printed by the following statements?
   
   .. sourcecode:: python

      mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
      print(23 in mydict)



.. mchoice:: mc11h
   :answer_a: 18
   :answer_b: 43
   :answer_c: 0
   :answer_d: 61
   :correct: b
   :feedback_a: Add the values that have keys greater than 3, not equal to 3.
   :feedback_b: Yes, the for statement iterates over the keys.  It adds the values of the keys that have length greater than 3.
   :feedback_c: This is the accumulator pattern.  total starts at 0 but then changes as the iteration proceeds.
   :feedback_d: Not all the values are added together.  The if statement only chooses some of them.
   
   
   What is printed by the following statements?
   
   .. sourcecode:: python

      total = 0
      mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
      for akey in mydict:
         if len(akey) > 3:
            total = total + mydict[akey]
      print(total)
   



