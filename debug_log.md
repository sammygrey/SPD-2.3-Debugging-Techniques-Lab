# Debug Log

**Explain how you used the the techniques covered (Trace Forward, Trace Backward, Divide & Conquer) to uncover the bugs in each exercise. Be specific!**

In your explanations, you may want to answer:

- What is the expected vs. actual output?
- If there is a stack trace, what useful information does it contain?
- Which technique did you use, on which line numbers?
- What assumptions did you have about each line of code, and which ones were proven to be wrong?

_Example: I noticed that the program should show pizza orders once a new order is made, and that it wasn't showing any. So, I used the trace forward technique starting on line 13. I discovered the bug on line 27 was caused by a typo of 'pzza' instead of 'pizza'._

_Then I noticed another bug ..._

## Exercise 1

### startup site using flask per normal

### when submitting a pizza order - TypeError: 'topping' is an invalid keyword argument for PizzaTopping, probably put topping instead of topping_type for the PizzTopping model

### ctrl f for topping

### error is on line 79 PizzaTopping(topping=topping_str) instead of PizzaTopping(topping_type=topping_str)

### new error Could not build url for endpoint '/'. Did you mean 'fulfill_order' instead?, probably exactly what it says

### have it redirect the url to home instead of / because thats nothing, but no past orders seem to show up now and no way to fulfill hmmmm

### divide and conquer - look at database, app, and html rendering

### html looks fine at a glance

### check database.db as it has been created - looks fine

### check app.py where orders are submitted - db is not committed lol

### new error - NOT NULL constraint failed: pizza.order_name

### looking at ouput crust type is fine but name and size dont seem to be non-null, look at html to see what these are actually called in the form

### they are called order_name and pizza_size, not name and size, easy fix

### pizzas show up but toppings are bugged

### thing is we are taking in an array of toppings so we want to use getlist for order submission to grab from the form

### we also dont wanna append all topping types to the pizza lol, also run this loop first so we can add them all when creating the object

### fulfill button works, everything is in working order

## Exercise 2

[[Your answer goes here!]]

## Exercise 3

[[Your answer goes here!]]
