..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Adding More Attributes to the Class
-----------------------------------

Lets improve the Account class by enabling it to keep a history of all its transactions (deposits and 
withdrawals). We add two new attributes: a list for the transactions and a starting balance for this 
statement period. Both of these attributes are initialized in the constructor. We also add the method 
``statement`` to display this history.

.. activecode:: c1k
    
    class Account:
        '''Account class to model bank accounts'''
        
        def __init__(self, name):
            '''Create a new account for owner name and a zero balance'''
            self.__owner = name
            self.__balance = 0.00
            self.__transactions = []
            self.__start = 0.00

        def getBalance(self):
            return self.__balance

        def deposit(self, amount):
            '''increase balance by a positive amount'''
            if amount >= 0:
                self.__balance += amount

        def withdraw(self, amount):
            '''reduce balance by amount but do not an allow overdraft'''
            if self.__balance >= amount:
                self.__balance -= amount

        def __str__(self):
            return "{} ${:,.2f}".format(self.__owner, self.__balance)

        def statement(self):
            '''list the transactions with the running balance'''
            bal = self.__start
            print('starting balance ${:>8,.2f}'.format(bal))
            
            print('ending balance   ${:>8,.2f}'.format(self.__balance))

    p = Account('Jan')
    p.deposit(150)
    p.withdraw(30)
    p.withdraw(20)
    p.statement()
          

.. admonition:: Extend this program

   * Modify the deposit and withdraw methods in the above activecode to append the amount to the 
     transaction list (for withdraw, append the negative of the amount).

   * Modify the statement method (between the two existing print statements) to iterate over the 
     list of transactions, displaying its amount and the balance after this transaction posts.

.. index:: class diagram

Class Diagram
~~~~~~~~~~~~~

Computer scientists often use diagrams to describe the design of their programs. One such diagram 
is a **UML Class Diagram**. It shows the design of one or more classes. Each class is represented 
with a rectangle that is composed of three parts:

* The name of the class

* A list of the attributes

* A list of the methods (with parameters)

.. image:: Figures/class1.PNG
