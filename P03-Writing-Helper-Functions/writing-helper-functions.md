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

# Run Tests
create("purple sox")
create("red cloak")

print(read(0))
print(read(1))

update(0, "purple socks")
delete(1)

print(read(0))

```

Call your new functions at the end of the file by adding:
```python
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
From the error it looks like the error is happening on line 21. The exciting thing about the + operator is that it does different things depending on the circumstance, but here we've confused it. When + sees two strings it will join them together so ```"a" + "b" ``` becomes ```"ab"```. But when + sees two integers or floats (Numbers without and with decimals respectively) it will add them mathematically so ```1 + 2 ``` becomes 3. 

On line 19 set ```index = 0 ```. 
Because we left off the quotes, python will see this 0 as an integer and try to do math with it but it can't add a number to a word mathematically, so it complains. If we make index a string (a sequence of text characters) by using quotes, then it will no longer increment it in our loop correctly.

We must turn our mathematical number into the character representation of that number before we can use the + operator for string manipulation.
Python provides built-in functions to allow for easy **type casting** -- which is converting from one type to another.

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

## More helper functions

We'll need more helper functions to be sucessful here still. We need one that marks our items as completed. 
Fortunately we have all the skills needed to write this function.

```python
def mark_completed(index):
    # Your Code here
```
Complete the function above. *Hint*: Add text to the front of the text that already exists to mark item as completed.

## Capturing User Input
In order to interact with the list we'll need to be able to accept user input from the terminal.
Use the input function to do this.

Lets create a function to prompt the user.

```python
def user_input(prompt):
    user_input = input(prompt)
    return user_input
```

Obviously we'll have to add additional options but for now we'll just leave it with these two options.

Lets also write a function that does something with the user input that we get. We'll need to check what the user gave us which we can do with the if..elif..else block. 

This where a good chunk of our actual code will reside. I'll start with a very simple decision tree that you will be able to flush out by yourself.


```python
def user_selection(function_code):
    # Create item
    if function_code == "C":
        input_item = user_input("Input item:")
        create(input_item)

    # Read item
    elif function_code == "R":
        item_index = user_input("Index Number?")

        # Remember that item_index must actually exist or our program will crash.
        # This is a good place to verify user input.
        read(item_index)

    # Print all items
    elif function_code == "P":
        list_all_items()

    # Catch all
    else:
        print("Unknown Option")
    
```
Notice that comparisons are done using the == syntax whereas = is the assignment sytax. You can add as many elif statements as you want

Add this function and comment out the tests that you wrote earlier.

The following lines should be added at the bottom to work with the function we just used.

```python
selection = user_input("Press C to add to list, R to Read from list and P to display list")
user_selection(selection)
list_all_items()
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

def user_selection(function_code):
    # User Selection Code here

# Run Tests
# create("purple sox")
# create("red cloak")
# ...
# ...
# list_all_items()

selection = user_input("Press C to add to list, R to Read from list and P to display list")
user_selection(selection)
list_all_items()
```

You should be able run the program once before it ends.

We only need a couple more additions to get this working properly.

When our program completes, everything we've done in memory is thrown out. We want to be able to keep the program open until we want to shut it down.

This is where our second type of loop will come in handy. We really just want to loop those last 3 lines until we want to quit. A while loop will do nicely here.

Congratulations - only one more section to go!