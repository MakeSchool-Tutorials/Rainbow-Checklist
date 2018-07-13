---
title: Create, Read, Update, and Destroy Functions
slug: crud
---
## Creating a Checklist
Here we're going to allocate space in memory that will be able to hold all the items in our checklist. This sounds harder than it will actually be.

Let's implement a simple checklist using a special Python data type called a **list**. If you're familiar with the concept of an array, then you're already familiar with the idea of a python list. 

A list can be thought of as a series of blocks in memory that live next to each other. You can fit data into any block that already exists, add additional blocks, remove unwanted blocks, and of course edit anything in the allocated blocks. Each block is referred to by its index number which starts at 0.

When we want to create a new item for our checklist we'll simply add a new block to our list and store our value there.

To the computer, our list can be simply thought of as the memory address that the list starts at. To us though coding memory addresses by hand is unnessesary so we can just refer to it by the name we wish to call it. This name is referred to generally as a **variable** because its value can change. Many other languages give you another option called a **constant** which cannot change after it's been created in memory but Python doesn't give us this feature. 

A variable simply points to a space in memory that is able to store something.

Variables can hold individual values, but they can also hold what are called **objects**. Our list is not a single piece of data like a number or a word -- it's an **object** -- that is it contains more than just the data we put in it. Along with the data in our list we are also given (for *nearly* free) code that helps us manage that data. We'll soon see how to access our data directly and also how to run the code or **methods** that are already included within our list object.

## Declaring Variables
So the following line
```python
checklist = list()
```
creates a list object in memory that we can refer back to by the name `checklist`.

In Python this line can also be written as 
```python
checklist = []
```
However using `checklist = list()` is more explicit so that is what I'll choose here.

As we'll see later, our list object already includes within it most of the code we'll need to work with it.

## Making our Code Reusable with Functions
Writing each command explicitly isn't a terribly useful way to program. Ideally you will want to be able to re-use as much code as possible. This means breaking it up into small chunks that can be called on when needed. These chunks of code are called **functions** and are how we will structure most of our program. 

A function is just a collection of code that allows for reuse and is declared as such:
```python
def my_fun_function(say_this):
    print(say_this)
```
Functions accept any number of values as **parameters** -- or inputs-- and can optionally return a value to whatever called the function in the first place. We'll see how to return a value back in a little bit.

This function when run will take a single parameter, `say_this`, as its input and print it to the console. Every line below the function declaration

 `
 def my_fun_function(say_this):
 `

must be indented to be included within that function. You can indent with spaces or tabs but once you choose one you can't mix the two.

Lets run our new function.

```
my_fun_function("Hello Worlds")
```

You'll see the output will be:

```
Hello Worlds
```

Lets create our first useful functions using what we learned when we ran the code above. 

## CRUD
### Create, Read, Update, and Destroy

So now that we have our checklist we will need to be able to use it. There are four main functions that need to happen in order for this list to be useful. We need to be able to Create, Read, Update, and Destroy items in our checklist.

## Create Function
We've seen how to create a function, but how to we add a new item to our checklist?

Add these lines to checklist.py and run the file in the terminal as explained in section 00 above.
```python
checklist = list()
checklist.append("Hello")
print(checklist)
checklist.append("World")
print(checklist)
```
You should see the output in the terminal:
```
['Hello']
['Hello', 'World']
```

So what's happening here?

* Line 1 creates a new empty list object and puts it in memory.
* Line 2 runs a chunk of code within that object and passes in the value we wish to add to our list.
* Line 3 prints the entire list to the console.
* Line 4 runs the same append code and passes "World" to our list.
* Line 5 prints the entire list again.

Python displays 'Hello', 'World' in brackets to tell you the items Hello and World are in a list.

So lets put this inside our new create function.
```python
def create(item):
    checklist.append("Hello")
```

This won't work the way we want because it will just add ```Hello``` for every item in the list. Lets update it a bit.

```python
def create(item):
    checklist.append(item)
```
And like magic you can add anything you want (within reason) to your list. Do you feel the power coursing through your fingers yet? No? Well just wait a bit then.

Lets create our next function -- read.

## Read Function

So now we have a list that we can add items to. How then do we access an item?
You can retrieve individual items in the list by using an index. Think of it as the block number the data resides in.
Indexes start at zero so to access the first block that was added, you'll use:

```python
checklist[0]
```

If `checklist` at the time you called this looked like `['Hello', 'World']`

Then this will be the output in the terminal.
```
Hello
```

It may seem odd to start a list at 0, but this is pretty standard in the industry due to some very nice lower level behavior that will be discussed in CS2.

So in order to retrieve a value from our list we'll need to have the index where the data lives. This should tell us that it should be a **parameter** in our new read function.

```python
def read(index):
    item = checklist[index]
    return item
```
`item = checklist[index]` will return the value that lives at that index in our checklist and save it in a memory location we named `item`. 
The function will then return the value that resides at the memory address we called `item`.

We can do a bit better though and stick it all on two lines:
```python
def read(index):
    return checklist[index]
```

## Update Function
How about updating an item in the list?

Try running these lines in Python:
```python
checklist = ['Hello', 'World']
checklist[1] = "Cats"
print(checklist)
```
The new line that is output in the terminal should be:

```
['Hello', 'Cats']
```
All this is doing is overwriting the data located in the second position of our list with the word "Cats".

Let's make a function out of this. Just like our last function we'll need the index of the item we'll need to update, but we'll also need to know what we need to update it with. This function will need an additional parameter.

```python
def update(index, item):
    checklist[index] = item
```

So that takes care of the first three letters, C, R, and U. Now we just the the last one - Destroy.

## Removing Items
Here we'll need to access a different chunk of code -- or **method** -- inside our object. Methods and functions are very similar concepts except that methods exist inside of objects and functions do not.

Enter the pop method.

Calling the pop method in our list will remove the last item in the list by default, unless of course we give it the index of the item we want to remove.

```python
checklist = ['Hello', 'World']
checklist.pop(1)
print(checklist)
```
This should output:
```
['Hello']
```
You can see that we've removed the second element in our list.

Lets turn this into a function like this:
```python
def destroy(index):
    checklist.pop(index)
```

Now that we have our main functions to work with our checklist we can start to make progress. There are also many more methods that you can access in this object as well as many other objects in Python. Check out the [python list documentation](https://docs.python.org/3/tutorial/datastructures.html) to see what other methods are available to you.

### Where do we go from here?

So we know that we're going to use a python list to keep our checklist in. We know how to CRUD our checklist -- so now lets make functions that we can call to make the process easier.

We'll need at least four functions.

## Testing
Our checklist.py file we wrote so far should be organized like this:
```python
checklist = list()

def create(item):
    # Create item code here

def read(index):
    # Read code here

def update(index, item):
    # Update code here

def destroy(index):
    # Destroy code here

```

Testing code is so important that we won't cover it in this tutorial in much depth at all. However normally our testing code would reside in another file and be run with an automated testing tool like pytest. Using a tool like pytest allows you be consistent with the process of verifying that functions work as they should. Instead of using pytest to interpret the result we'll just use our eyeballs and the terminal.

Here though we will create a function that will house all of our testing code. That way we can toggle it on and off easily when needed.

```python
def test():
    # Add your testing code here
```

Test the functions you made by calling them with different values and checking the result.

Add these function calls to your new `test` function:
```
create("purple sox")
create("red cloak")

print(read(0))
print(read(1))

update(0, "purple socks")
destroy(1)

print(read(0))
print(read(1))

```

Call your new testing function by adding `test()` to the bottom of your file.

Your program should be structured like this:

```python
checklist = list()

def create(item):
    # Create item code here

def read(index):
    # Read code here

def update(index, item):
    # Update code here

def destroy(index):
    # Destroy code here

def test():
    # Your testing code goes here

test()
```

You should see the following output:
```
purple sox
red cloak
purple socks
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in read_item
IndexError: list index out of range
```
We see an error because we tried to access the second item in a one item list. The last line of the error tells us this by saying the index was out of range.
This may be something we'll have to think about if we were going to implement this in production. If this function were called with an invalid index value our program would crash and people would be sad. As a stretch challenge you can update any applicable functions that we have made with the ability to verify that all index values are accurate.

Remove the line that throws the error so we can move on.