---
title: Create, Read, Update, and Destroy Functions
slug: crud
---
## Creating a Checklist

Everything that we need to do will exist in the computer's memory somewhere. First we need to be able to allocate some of that memory to hold all the items in our checklist. This sounds harder than it will actually be.

Try this line in interactive mode. (See **Testing Thing Out** in Section 00 to do this.) 
```python
checklist = list()
```

On the following line type:
```
checklist
```
You'll see this output appear.
```
[]
```

Interactive mode assumes you want to view the contents of the memory space called `checklist` when you write out its name on a line by itself. 

Anything that our list contains would show up between the brackets, but our list is empty so we only see brackets.

We can implement a simple checklist using a special Python **data type** called a **list**. If you're familiar with the concept of an array, then you're already familiar with the idea of a python list. 

A list can be thought of as a series of blocks in memory that live next to each other. You can fit data into any block that already exists, add additional blocks, remove unwanted blocks, and of course edit anything in the allocated blocks. Each block is referred to by its index number which starts at 0.

When we want to create a new item in our checklist we'll simply add the next block of memory and store our value there. Python behind the scenes is smart enough to make sure our blocks are the right size and that there's space to add as many blocks as we want.  

>
> A **data type** is the classification that specifies the kind of data that exists somewhere. Python is considered a **loosely typed** language which means you don't have to tell the computer the type of value it should expect to store in memory. This convenience has some drawbacks that we will encounter later.
>

## Variables 
A variable simply points to a space in memory that is able to store something. It can hold an individual value like a number, but it can also hold what is called an **object**. Our list is not a single piece of data like a number or a word -- it's an **object**. This means it contains more than just the data we put in it. Along with the data in memory, objects supply (for *nearly* free) code that helps us manage that data. 

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
The first example is more explicit so that is what I'll use.

As we'll see later, our list object already includes within it most of the code we'll need to work with it.

## Making our Code Reusable with Functions
Writing each command explicitly isn't a terribly useful way to program. Ideally you will want to be able to re-use as much code as possible. This means breaking it up into small chunks that can be called on when needed. These chunks of code are called **functions** and are how we will structure most of our program. 

A function is just a collection of code that allows for reuse and is written like this:
```python
def my_fun_function(say_this):
    print(say_this)
```
Functions accept any number of values as **parameters** -- or inputs-- and can optionally return a value to whatever called the function in the first place.

This function when run will take a single parameter, `say_this`, as its input and print it to the console. Every line below the **function declaration** must be indented to be included within that function. You can indent with spaces or tabs but once you choose one you can't mix the two.

> A **function declaration** is the line that tells python the name of the function along with any parameters it needs. Here  
>
>`
> def my_fun_function(say_this):
> `
> 
> is the function declaration.

Lets run our new function.

```
my_fun_function("Hello World")
```

You'll see the output will be:

```
Hello World
```

Lets create our first useful functions using what we learned when we ran the code above. 

## Create, Read, Update, and Destroy

Now we have our checklist but we can't use it yet. There are four main functions that we need to write in order for this list to be useful. These functions are so common that we refer to them by the acronym CRUD -- create, read, update, and destroy.

## Create
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

This won't work the way we want because every item in our list will just be ```Hello```. 

Can you guess what our new update will be?

```python
def create(item):
    checklist.append(item)
```

Hopefully you can see that Python interprets anything in quotes as an actual value - specifically the **string** data type. Whereas if you leave off the quotes it will look for a variable of that name (unless its a number in which case Python will treat it as such). 

In the second example we are referring to the variable we declared in the function declaration.

Just like magic you can add anything you want (within reason) to your list. Do you feel the power coursing through your fingers yet? No? Well just wait a bit then.

Lets create our next function -- read.

## Read

So now we have a list that we can add items to. How then do we access an item?
You can retrieve individual items in the list by using an index. Think of it as the block number the data resides in.
Indexes start at zero so to access the first block that was added, you'll use:

```python
checklist[0]
```

If `checklist` at the time you called this looked like `['Hello', 'World']`

Then `checklist[0]` would return:
```
Hello
```

It may seem odd to start a list at 0, but this is pretty standard in the industry due to some very nice features that will be discussed in CS2.

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


## Update
Try running these lines in Python:
```python
checklist = ['Hello', 'World']
checklist[1] = "Cats"
print(checklist)
```
You should see:

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
Here we'll need to access a different chunk of code -- or **method** -- inside our object. Methods and functions are very similar concepts except that methods are what we call blocks of code inside of objects. Methods are called using **dot notation** and functions are not.

Enter the pop method.

Calling the pop method in our list will remove the last item in the list by default. If we want a different item we must specify it. 

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

There are many more methods that are available inside the Python list object. Check out the [python list documentation](https://docs.python.org/3/tutorial/datastructures.html) to see what other methods are available to you.

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

Your program should be structured something like this:

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
(Don't paste this into your code, it's only to serve as an overview of what you should already have.)

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