---
title: Putting it all together
slug: putting-it-together
---
# The While Loop
Running a chunk of code over and over again is so common that we're given many ways of accomplishing this one task. Many people have their own preferred looping strategy and there are many valid ways to approach a single problem. We've seen in our `list_all_items` helper function a way to loop over a specific number of values, but what if we don't know how many times we'll need to loop over a given piece of code?

The `while` loop will help us out in this case as it will continue to loop over a section of code until a specified condition is met. Here our condition will be met when the user selects the Q option in the terminal.

 The syntax for the while loop is as follows:

```python
while condition:
    #Run this code
```

We'll need a condition that starts off as true but can change to false during runtime. 
Lets wrap our statements in the while loop like this:

```python
running = True
while running:
    selection = user_input("Press C to add to list, R to Read from list and P to display list")
    user_selection(selection)

```
Here we have set a variable named running to ```True```. On every run the while loop will check the value of `running` and it will return back as True therby continuing the loop. This is called an infinite loop and it is where Apple decided to build their headquarters.

This code will never finish running so we need a way to set running to False somewhere.

Also as an aside, you'll notice that in python the difference between True and true is that True evaluates to a boolean whereas true will evaluate to a variable name. If true was never used as a variable name then python will complain that it can't find true.

## Fix the Infinite Loop
An easy way to fix this is to add an option to our user_selection function that allows for the user to quit.

What we should do is have the function return a value of True for every option except for one. See if you can do this yourself.

Here is hint of what the updated function will look like:
Here when you hit Q, we'll hit a block of code we want to execute that will allow us to quit.

```python
def user_selection(function_code):
    # Create item
    if function_code == "C":
        input_item = user_input("Input item:")
        create_item(input_item)
    # Read item
    elif function_code == "R":
        item_index = user_input("Index Number?")
        #Remember that item_index must actually exist or our program will crash.
        # This is a good place to verify user input.
        read_item(item_index)

    # Print all items
    elif function_code == "P":
        list_all_items()
    elif function_code == "Q":
        # This is where we want to stop our loop
        return False
    else:
        #Catch all
        print("Unknown Option")
    return True
```
Then inside our while loop we can set our running variable to False thereby exiting the while loop.

```python
running = True
while running:
    selection = user_input("Press C to add to list, R to Read from list, P to display list, and Q to quit")
    running = user_selection(selection)
```
This will now let you continue to use the checklist until you don't need it anymore.

This is what your updated file look similar to.
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

def user_selection(function_code):
    # User Selection Code here

def test():
    # Your testing code goes here

# Run Tests
# test()

running = True
while running:
    selection = user_input("Press C to add to list, R to Read from list, P to display list, and Q to quit")
    running = user_selection(selection)
```

At this point you should have a simple working that looks like this
![]()

## One last thing
You'll notice that if you run the R option an error shows up. This is similar to one of the other errors we've seen in this tutorial. See if you can fix the error in question.

## Finish things up
The remainder of the program can be finished with the concepts you've already learned here.
Todo:
* Fix TypeError that occurs when running option 'R'
* Add update and destroy options to user_selection function

Stretch Challenges:
* Make user prompt easier to read by clearing the output between user selection.
* Handle errors caused by user error that might pop up.
* Add function that un-checks a checked item in the list


## Conclusion
This tutorial covered a lot of material. This first run through python may feel overwhelming but with additional practise and exposure you'll start to gain a mastery of programming concepts that will lead to more powerful concepts down the road. You're now firmly on your way to becoming your own super hero.