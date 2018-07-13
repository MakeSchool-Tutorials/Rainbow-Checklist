---
title: Creating Helper Functions
slug: helper-functions
---
## Helper Functions
You may see a need for a few more functions to help us out with our checklist.

Right now we can see a single item if we know its index, but we should be able to see the entire list.

In order to get the entire list we'll need to get every individual item in the list. This sort of operation is done so frequently that we're given many different tools to do it. This tutorial will make use of two different types of loops: for and while.

The for loop in python is simple and powerful at the same time. Python takes care of a number of things for us that other languages do not. The syntax that we'll use is as follows:

```python
for list_item in checklist:
    #Do something
```

Here python will iterate over all the items in checklist and pass each value into the code block below it as the value list_item.
I chose to use "list_item" but it could be valid variable syntax. Just as our functions needed to be indented so too do the statements you want to run on every iteration.

Let's put it in a function.

```python
def list_all_items():
    for list_item in checklist:
        print(list_item)
```

This code will loop over every item in the checklist and run the built-in print function on every item, but it only prints out the list item. We have a few functions that require an index number so we should display this as well. We'll have to add a bit of logic to get this number. Change the function to add the index.

```python
def list_all_items():
    index = 0
    for list_item in checklist:
        print(index + list_item)
        index += 1
```

Incrementing by an amount is done so often there is a shortcut for it. The += syntax takes the current value and adds to it. Play around with it in interactive mode to see how it works with integers, decimals, and strings.

At this point your python script should look like this:

```python
# Create our Checklist
checklist = list()


# Define Functions
def create(item):
    # Create item code here

def read(index):
    # Read code here

def update(index, item):
    # Update code here

def destroy(index):
    # Destroy code here

def list_all_items():
    # Code to list all items in list

def test():
    # Your tests here

test()

```

Call your new functions by adding this function call to your test function:
```python
list_all_items()
```

Your testing function should look like this:

```python
def test():
    create("purple sox")
    create("red cloak")

    print(read(0))
    print(read(1))

    update(0, "purple socks")
    destroy(1)

    print(read(0))
    list_all_items()
```

You'll see when you run this that the output has an error.

```
purple sox
red cloak
purple socks
Traceback (most recent call last):
  File "./checklist.py", line 36, in <module>
    list_all_items()
  File "./checklist.py", line 21, in list_all_items
    print(index + list_item)
TypeError: unsupported operand type(s) for +: 'int' and 'str'
```
From the error it looks like the error is happening on line 21. Your error may exist on a different line than mine depending on where your `list_all_items` function exists. 

The exciting thing about the `+` operator is that it does different things depending on the circumstance, but here we've confused it. When `+` sees two strings it will join them together so ```"a" + "b" ``` becomes ```"ab"```. But when `+` sees two integers or floats (Numbers without and with decimals respectively) it will add them mathematically so `1 + 2` becomes 3. 

Line 19 set `index = 0`. 

Because we left the quotes off when setting index to 0 Python will interpret the value that index represents as a number - specifically a type of number called an **integer**. An integer is simply a number without a decimal whereas a **float** is a number with a decimal. We need our index to be an integer so can do math with this number. However when the `+` operator sees a number and some text it cannot tell which operation we intend to make. Should it do math, or string manipulation? In order to properly use the `+` operator we must convert our number to text. In computer science this text is called a **string** which is just a sequence of characters next to each other. If we make our index variable a string (a sequence of text characters) by using quotes, then it will no longer increment it in our loop correctly.

We must temporarily convert our mathematical number into the character representation of that number before we can use the + operator for string manipulation.
Fortunately Python provides built-in functions to allow for easy **type casting** -- which is converting from one type to another. In this case we want to cast an integer as a string.

We can fix this function by adding a few things to our print statement.

```python
def list_all_items():
    index = 0
    for list_item in checklist:
        print(str(index) + list_item)
        index += 1
```

This will fix our error and gives us:
```
purple sox
red cloak
purple socks
0purple socks
```

Feel free to adjust the formatting to print a little nicer to the terminal.

## Mark Completed
We need a helper function that marks our items as completed. 
Fortunately we have all the skills needed to write this function.

```python
def mark_completed(index):
    # Add code here that marks an item as completed
```
Complete the function above. *Hint*: Add a character to the front of the checklist item that denotes an item as completed.

All we need to do is append some text to the item that we want to mark as checked. Let's use the character √ to indicate whether an item is marked as completed or not.

>[info]
>Look at how we implemented the update and read functions to get an idea about how to interact with the item you want to work with. Use the `+` operator to append a checkmark to the front of the item in the checklist.

## Feature Selection
Let's also write a function that allows us to select which functions we want to run. We'll need to control the flow of our program by calling some functions sometimes and other functions at other times. We can put all this in it's own separate function to keep our program easier to follow.

The typical way to control which parts of your code are executed is with  `if..elif..else` statements. You'll be able to easily add additional `elif` blocks in order to add the functionality to complete this tutorial.

```python
def select(function_code):
    # Create item
    if function_code == "C":
        input_item = user_input("Input item:")
        create(input_item)

    # Read item
    elif function_code == "R":
        item_index = user_input("Index Number?")

        # Remember that item_index must actually exist or our program will crash.
        read(item_index)

    # Print all items
    elif function_code == "P":
        list_all_items()

    # Catch all
    else:
        print("Unknown Option")
    
```
Notice that comparisons are done using the `==` syntax whereas `=` is the assignment syntax. You can add as many `elif` statements as you will need.

Test this code by adding calls to this function inside your test function.

In order to fully test this function you'll want to be sure that your testing code will run each of your `elif` code blocks.

## Capturing User Input
In order to choose which function to run we'll need to be able to accept user input from the terminal.

Use the built-in `input` function to do this.

Let's create a function to prompt the user.

```python
def user_input(prompt):
    user_input = input(prompt)
    return user_input
```

Having user input exist in its own function allows us to know where to look if anything unexpected happens. User input is notoriously tricky and is typically sanitized in some way to prevent accidental and malicious input that may crash or exploit the system that you've spent so much time on. We will included a parameter that allows us to reuse this function with any message that needs to be delivered to our user.
#####

```python
selection = user_input("Press C to add to list, R to Read from list and P to display list")
user_selection(selection)
```

This will give us one run through, but we'll see that it's working.

Your checklist.py should look like this:
```python
# Create our Checklist
checklist = list()

# Define Functions
def create(item):
    # Create item code here

def read(index):
    # Read code here

def update(index, item):
    # Update code here

def destroy(index):
    # Destroy code here

def list_all_items():
    # List all items code here

def mark_completed(index):
    # Your code here

def user_input(prompt):
    # Get user input here

def select(function_code):
    # User Selection Code here

def test():
    # Test your functions here

# Run Tests
# test()

selection = user_input("Press C to add to list, R to Read from list and P to display list")
user_selection(selection)
```

You should be able run the program once before it ends.

We only need a couple more additions to get this working properly.

When our program completes, everything we've done in memory is thrown out. We want to be able to keep the program open until we want to shut it down.

This is where our second type of loop will come in handy. We really just want to loop those last 3 lines until we want to quit. A while loop will do nicely here.

Congratulations - only one more section to go!
