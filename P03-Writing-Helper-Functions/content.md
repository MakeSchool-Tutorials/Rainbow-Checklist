---
title: Creating Helper Functions
slug: helper-functions
---
## Helper Functions
You may see a need for a few more functions to help us out with our checklist.

Right now we can see a single item if we know its index, but we should be able to see the entire list.

## list_all_items 
```python
for list_item in checklist:
    #Do something
```
In order to view the entire list at once we'll need to get every individual item in the list. We'll need to run a bit of code over and over again in order for this to work. We do this so frequently that we're given many different tools to work with. We will make use of two different types of loops in this tutorial-- the **for** loop and **while** loop.

The **for** loop in python is simple and powerful at the same time. Python takes care of a number of things for us that other languages do not. The syntax that we'll use is as follows:



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

Incrementing by an amount is also done so often that there is a shortcut for it. The += syntax takes the current value and adds some value to it. Play around with it in interactive mode to see how it works with integers, decimals, and strings.

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

When you run it you should encounter an error.

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
The last line of our error tells us what is wrong.

```
TypeError: unsupported operand type(s) for +: 'int' and 'str'
```


Your error may exist on a different line than mine depending on where your `list_all_items` function exists. 

The fun thing about the `+` **operator** is that it does different things depending on the circumstance. Here we're trying to do something it's not prepared to do. 

When `+` sees two strings it will join them together so ```"a" + "b" ``` becomes ```"ab"```. But when `+` sees two integers or floats it will add them mathematically so `1 + 2` becomes 3. 

```
def list_all_items():
    index = 0
    for list_item in checklist:
        print(index + list_item)
        index += 1
``` 
This function is our culprit.

Our problem is that `+` doesn't work with different data types.

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
This works okay but there is another cleaner way to write this. 

Just as our list object had methods that we could use to work with our list, Python strings have methods within them that allow you to work with strings. 

```python
print("{} {}".format(index, list_item))
```

Here we're calling the format method on a string. The format method will take care of replacing the curly braces with the variables we provide it. 

You may wish to replace the print statement in the above function with the updated print statement using the format method.

Feel free to adjust the formatting to print the way you want in the terminal.
>
>As a stretch challenge try adding colors to the terminal output.
>
## mark_completed
We need a helper function that marks our items as completed. 
Fortunately we have all the skills needed to write this function.

```python
def mark_completed(index):
    # Add code here that marks an item as completed
```
Complete the function above. *Hint*: Add a character to the front of the checklist item that denotes an item as completed.

All we need to do is append some text to the front of the checked item in the list. Let's use the character √ to indicate whether an item is marked as completed or not.

So if Captain Rainbow needs to wear 

```Yellow Shoes```

After he marks his shoes off the list he should see

```√Yellow Shoes```

You can type the character by pressing option-v together.

>[info]
>Look at how we implemented the update and read functions to get an idea about how to interact with the item you want to work with. Use the `+` operator or the string format methods described in the list_all_items function to append a checkmark to the front of the item in the checklist.

Remember that you need the index of the item you want to work with.

Can you use an existing function to update a value in the checklist with a new value?

## select
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
Let's also write a function that allows us to select which functions we want to run. 

The typical way to control which parts of your code are executed is with  `if..elif..else` statements. You'll be able to easily add additional `elif` blocks to increase the functionality of your program.

Notice that comparisons are done using the `==` syntax whereas `=` is the assignment syntax.

Test this code by adding calls to this function inside your test function like this.

```python
def test():
    # Your testing code here
    # ...
    # Call your new function with the appropriate value
    select("C")
    # View the results
    list_all_items()
    # Call function with new value
    select("R")
    # View results
    list_all_items()
    # Continue until all code is run
```

In order to fully test this function you'll want to be sure that your testing code will run each of your `elif` code blocks.

Don't delete any of the tests that you've already written. All tests should be run to make sure that everything still works. In a later tutorial we'll see how to automate this process in cases where we have a lot of tests or when they take awhile to complete.

## user_input function
In order for our program to be useful we'll need to be able to accept user input from the terminal. We will use the built-in `input` function to do this.

Let's create a function to prompt the user.

```python
def user_input(prompt):
    # the input function will display a message in the terminal 
    # and wait for user input.
    user_input = input(prompt)
    return user_input
```

Checking for user input inside a dedicated function allows us to know where to look if anything unexpected happens. User input is notoriously tricky and is typically sanitized in some way to prevent accidental and malicious input that may crash or exploit your system. We will include a parameter that allows us to reuse this function with any message that needs to be delivered to our user.

Call this function with your other tests this way:

```python
user_value = user_input("Please Enter a value:")
print(user_value)
```

## Overview
So far we've created and tested every one of the functions that we'll need though we don't really have a working program yet. 

Your checklist.py should be arranged like this:
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

def select(function_code):
    # User Selection Code here

def user_input(prompt):
    # Get user input here

def test():
    # Test your functions here

# Run Tests
 test()
```

We only need a couple more additions to get this working properly.

When our program completes, everything we've done in memory is thrown out. We want to be able to keep the program open until we want to shut it down.

This is where our second type of loop will come in handy. We really just want to loop a few lines of code until our user wants to quit. This brings us to our last section -- the while loop.
