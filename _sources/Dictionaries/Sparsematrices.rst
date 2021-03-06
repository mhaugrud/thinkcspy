..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dict-5-
   :start: 1

.. index:: matrix

Matrices
--------

A matrix is a two dimensional collection, typically thought of as having rows and columns of data. In the
*More About Iteration* chapter, we saw how an image is a two dimensional collection of pixels. One of the 
easiest ways to create a matrix is to use a list of lists.  For example, consider the matrix shown below.  




.. image:: Figures/sparse.png
   :alt: sparse matrix 

We can represent this collection as five rows, each row having five columns.  Using a list of lists representation, we will have a list of five items, each of which is a list of five items.  The outer items represent the rows and the items in the nested lists represent the data in each column.


.. activecode:: tdt
    
    matrix = [[0, 0, 0, 1, 0],
              [0, 0, 0, 0, 0],
              [0, 2, 0, 0, 0],
              [0, 0, 0, 0, 0],
              [0, 0, 0, 3, 0]]

    print(matrix[0][3])
    print(matrix[2][1])
    print(matrix[1][2])


One thing that you might note about this example matrix is that there are many items that are zero.  In fact, 
only three of the data values are nonzero.  This type of matrix has a special name.  It is called a 
`sparse matrix <http://en.wikipedia.org/wiki/Sparse_matrix>`__.

Since there is really no need to store all of the zeros, the list of lists representation is considered to be inefficient. An alternative representation is to use a dictionary. For the keys, we can use tuples that 
contain the row and column numbers. Here is the dictionary representation of the same matrix.

.. sourcecode:: python
    
    matrix = {(0, 3): 1, (2, 1): 2, (4, 3): 3}

We only need three key-value pairs, one for each nonzero element of the matrix. Each key is a tuple
representing the row and column numbers, and each value is an integer.

To access an element of the matrix, we can use the ``[]`` operator::
    
    matrix[(0, 3)] 

Notice that the syntax for the dictionary representation is not the same as the syntax for the nested list representation. Instead of two integer indices, we use one index, which is a tuple of integers.

We can omit the parentheses for the tuple::
    
    matrix[0, 3] 

There is a small problem. If we specify a key that is not in the dictionary, ``None`` is returned. The 
alternative version of the ``get`` method solves this problem. The first argument is the key.  The second 
argument is the value ``get`` should return if the key is not in the dictionary.

.. activecode:: tdu

   matrix = {(0, 3): 1, (2, 1): 2, (4, 3): 3}

   print(matrix[0,3])
   print(matrix.get((0,3)))
   print(matrix.get((0,3), 'key not found'))
   print(matrix.get((1,2)))
   print(matrix[1,2])

.. admonition:: Correct the error ...

   - Run and notice that lines 3 through 6 produce valid results.

   - Line 7 causes a run-time error since (1,2) is not a key in the dictionary. Comment out this line.

   - In line 5, change ``0,3`` to ``1,2``. Run and notice there are no errors.

   - In this sparse matrix all the elements not defined in the dictionary have a value of zero. In line 5, 
     change ``'key not found'`` to ``0``. Run and notice the proper value is returned for a key not present 
     in the dictionary.

In the above example, the tuple keys consist of two integers: first the row followed by the column. This 
closely corresponds to the indexing for the nested list example shown in the activecode at the top of
this page.

Suppose instead we want to use tuple keys with the column first followed by the row. This corresponds to
the Cartesian system where we specify a point by its x (column) and y (row) coordinates. The activecode
below demonstates this with the same matrix shown at the top of the page and placing (0,0) at the upper
left corner and (4,4) at the lower right. (This is the arrangement of pixels in an image.)

.. activecode:: tdv

   matrix = {(3, 0): 1, (1, 2): 2, (3, 4): 3}

   x = int(input('x coordinate'))
   y = int(input('y coordinate'))
   print(matrix.get((x,y),0))

.. admonition:: Modify the program ...

   - Run the activecode with several different values for x and y. Compare the output with the picture
     at the top of this page.
   - Edit line one so (0,0) is at the lower left corner and (4,4) at the upper right. (This is the 
     conventional arragement of points in the Cartesian coordinate system.)

