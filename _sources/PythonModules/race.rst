
..  Copyright (C) 2011  Brad Miller and David Ranum
    Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Turtle Race
===========


We are going to work step by step through the problem of racing turtles.  The idea is that we want to create two or more turtles and have them race across the screen from left to right. The turtle that goes the farthest is the winner.

There are several different, and equally plausible, solutions to this problem. Let's look at what needs to be done, and then look at some of the options for the solution.  To start, let's think about a solution to the simplest form of the problem, a race between two turtles. We'll look at more complex races later.  

When you are faced with a problem like this in computer science it is often a good idea to find a solution to a simple problem first and then figure out how to make the solution more general.

Here is a possible sequence of steps that we will need to accomplish:

#. Import the modules we need

#. Create a screen

#. Create two turtles

#. Move the turtles to their starting positions

#. Send them moving across the screen

Here is the Python code for the first 4 steps above

.. activecode:: slf
   :nocodelens:

   import turtle              # 1.  import the modules
   import random
   wn = turtle.Screen()       # 2.  Create a screen
   wn.bgcolor('lightblue')

   lance = turtle.Turtle()    # 3.  Create two turtles
   andy = turtle.Turtle()
   lance.color('red')
   andy.color('blue')
   lance.shape('turtle')
   andy.shape('turtle')

   andy.up()                  # 4.  Move the turtles to their starting point
   lance.up()
   andy.goto(-180,20)
   lance.goto(-180,-20)

   # your code goes here

   wn.exitonclick()


Now, you have several choices for how to fill in code for step 5. Here are some possibilities to try.  Try coding each of the following in the box above to see the different kinds of behavior.

#. Use a single call to ``forward`` for each turtle, using a random number as the distance to move.

#. Create a for loop, using a random number for the parameter passed to the range function.  Inside the for loop move one of the turtles forward by one unit. Make another loop to do the same with the other turtle.

#. Create a single `for loop` using something like 150 or 200 as the range parameter. Inside the `for loop`, generate a small random number and move a turtle forward by that amount. Generate another random number and move the the other turtle forward by that amount.

In all of these options, the random numbers are whole numbers. So we should use the ``randrange`` function.

But, which of these options is better?  Which is most correct?  These are excellent questions. Option 1 is certainly the simplest, but it isn't very satisfying as far as a race is concerned.  Each turtle simply moves their distance on their turn.  That is not very satisfying as far as a simulated race goes.  Option 2 ends up looking a lot like option 1
when you run it.  Option 3 is probably the most 'realistic' assuming realism is very important when we're talking about a simulated race of virtual turtles.

.. admonition:: Complete the program ...

   Type in instructions (between # your code goes here and wn.exitonclick()) to implement Option 3. It requires 3-5 lines of code. Experiment with values for the random range to move the turtles. It should be quite small so that the turtles do not consistently move off the screen.
   

You may be thinking why can't each turtle just move forward until it crosses an artificial finish line?  Good question!  We'll get to the answer to this, and look at the program in a later lesson when we learn about something called the ``while loop``.
