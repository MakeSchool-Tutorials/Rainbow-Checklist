---
title: Putting it all together
slug: putting-it-together
---
# The While Loop
Running a chunk of code over and over again is so common that we're given many ways of accomplishing this one task. Many people have their own preferred looping strategies and there may be many valid ways to approach any particular problem. We've seen in our `list_all_items` helper function a way to loop over a specific number of values, but what if we don't know how many times we'll need to loop over a given piece of code?

The `while` loop will help us out in this case as it will continue to loop over a section of code until a specified condition is met. Here our condition will be met when the user selects the Q option in the terminal.

 The syntax for the `while` loop is as follows:

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
    select(selection)

```
Here we have set a variable named running to ```True```. On every run the `while` loop will check the value of `running` and it will return back as True therby continuing the loop. This is called an **infinite loop** -- that is a loop that does not end -- and it is where Apple decided to build their headquarters.

This code as it is will never finish running so we'll need a way to set `running` to False somewhere.

## Fix the Infinite Loop
An easy way to fix this is to add an option to our `select` function that allows for the user to quit.

What we should do is have the function return a value of True for every option except for one. Let's set Q to Quit our program.

Here is a bit of what the updated function will look like.
Notice when the user hits Q, they'll hit a block of code that will immediately return False.

```python
def select(function_code):
   
    if function_code == "C":
        #Create item in checklist here
    
    elif function_code == "R":
        # Read item in checklist here

    elif function_code == "P":
        # Print all items here

    elif function_code == "Q":
        # This is where we want to stop our loop
        return False
    else:
        #Catch all
        print("Unknown Option")
    return True
```
Then inside our `while` loop we can set our running variable to the returned value of our `select` function thereby exiting the while loop.

```python
running = True
while running:
    selection = user_input("Press C to add to list, R to Read from list, P to display list, and Q to quit")
    running = select(selection)
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

def select(function_code):
    # User Selection Code here

def test():
    # Your testing code goes here

# Run Tests
test()

running = True
while running:
    selection = user_input("Press C to add to list, R to Read from list, P to display list, and Q to quit")
    running = select(selection)
```

At this point you should have a simple working checklist that looks like this
![](rainbow_checklist_running.gif)

## Finish things up
The remainder of the program can be finished with the concepts you've already learned here.

Items left for you to do:
* Add read, update and destroy options to the select function.
* Allow for case insensitive feature selection.
* Handle errors caused by invalid user input (invalid indexes).

Was this too easy? 
Here are some stretch challenges :
* Make the user prompt easier to read by clearing the terminal output between user selections.
* Add function that un-checks a checked item in the list.
* Display colored text in terminal.


## Conclusion
Here we've seen how to approach designing a simple application. We started by defining the features we needed with user stories. Then we took those stories and implemented the features we needed as functions that could be executed. All our functions were thoroughly tested so that we knew that all our code was in working order before shipping to the user. 

We also saw that **objects** can contain both data and code that can be executed. Next we'll explore how to create our own objects and unlock the power of object oriented programming. In addition, we'll explore more testing tools that help us to write code with fewer bugs.