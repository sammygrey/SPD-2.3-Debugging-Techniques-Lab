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

### same as last time, run as intended first

### internal server error upon submission - tracing error to /results with city

### looking at home and results the city variable is referred to as city, not users_city, changing this

### further errors regarding the city in the json but json works lets just print it - nothing to geolocate

### problem with putting city in header, just put it in as part of the url as a query string

### still error, probably stuff is called wrong from json, but printing the json we can see the correct way to call it

### weather is fine, temp is part of main and called temp not temperature, humidity is fine, wind speed is fine, everything else is fine

### new error ValueError: Invalid format string, this is a problem with date strf in the html

### working backwards the problem seems to be with %-d which is now deprecated and %e has taken its place, same problem with %-I replaced with %H and %I respectively

### everything else is in working order

## Exercise 3

### this ones not a webapp its gonna be a lot faster lol

### prints list of nums then list index out of range prolly an obo error, problem is in merge sort function

### iterators in while loop with no bounds, bad idea for looping thru an array

### added bounds for i and j, not needed for k, fixed error on line 38 calling right_side[i] when its iterator is j

### new error is for binary search - list indices must be integers or slices, not float

### just add double / to truncate when solving for midpoint

### everything is now in working order, maybe add disclaimer that mergesort list is being sorted from high to low but not my job
