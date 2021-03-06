.. index:: inheritance, inheritance; augmentation

More Inheritance
----------------


Augumentation
~~~~~~~~~~~~~

Now suppose our bank offers savings accounts. This type of Account accrues (earns) interest based on 
its balance.

We start by saying that ``Savings`` is a child class of ``Account``. We add attributes for the amount 
of interest paid and the interest rate (at the class level). We also include an ``accrue`` method to 
pay interest.


.. activecode:: c2h
    
    class Account:
        def __init__(self, name):
            self.__owner = name
            self.__balance = 0.00

        @property
        def balance(self):
            return self.__balance

        def deposit(self, amount):
            self.__balance += amount

        def withdraw(self, amount):
            if self.__balance >= amount:
                self.__balance -= amount

        def __str__(self):
            return "{} ${:,.2f}".format(self.__owner, self.__balance)

    class Savings(Account):
        '''Savings inherits everything from Account'''
        __rate = 0.01  #the saving account interest rate
        def __init__(self, name):
            self.__intPaid = 0.0
            Account.__init__(self, name)
       
        def accrue(self):
            '''calculate and deposit interest'''
            interest = Savings.__rate * self.balance
            self.__intPaid += interest
            self.deposit(interest)

        @property
        def intpaid(self):
            return self.__intPaid
        

    a = Savings('Jan')
    a.deposit(1000)
    print('{} total interest:{}'.format(str(a), a.intpaid))
    a.accrue()
    print('{} total interest:{}'.format(str(a), a.intpaid))
    a.accrue()
    print('{} total interest:{}'.format(str(a), a.intpaid))


.. note::
   This form of inheritance is called **augmentation**. The child class has a method (with a name
   different than any in the parent class) giving it a new capability not available in the parent. 

.. index:: class diagram; inheritance

Class Diagram with Inheritance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The arrow in this class diagram indicates inheritance. The sub-classes inherit the attributes and methods 
of the super-class. The sub-classes can have additional attributes or methods. If a sub-class has a
method with the same name as one in the super-class, it overrides the super-class method.

.. image:: Figures/class2.PNG



