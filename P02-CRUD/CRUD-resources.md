---
title: Create, Read, Update, and Destroy Functions
slug: crud
---
## Creating a Checklist

Let's implement a simple checklist using a special Python data type called a list. If you're familiar with the concept of an array, then you're already familiar with the idea of a python list. 

A list can be simply thought of as a series of blocks of memory that live next to each other. You can fit data into any block that already exists, add additional blocks, remove unwanted blocks, and of course edit anything in the allocated blocks. Each block is referred to by its index number which starts at 0.

When we want to create a new item for our checklist we'll simply add it as an element in our list.

To the computer, our list can be simply thought of as the memory address that the list starts at. To us though coding memory addresses by hand is unnessesary so we can just refer to it by the name we wish to call it. This name is referred to generally as a variable. 

A variable simply points to a space in memory that is able to store something.

So the following line

```python
checklist = list()
```
allocates space in memory to hold a list "object" and refers to that memory address by the name checklist.


In Python this can also be written as 

```python
checklist = []
```
However using list() is clearer when you need to come back to this code in 6 months because your boss wants to change something.

Variables can hold individual values, but they can also hold what are called objects. Our list is not a single piece of data like a number or a word -- it's an object -- that is it contains more than just the data we put in it. Along with the data in our list we are also given (for ** nearly ** free) code that helps us manage that data. 

## CRUD
### Create, Read, Update, and Destroy

So now that we have our checklist we will need to be able to use it. There are four main functions that need to happen in order for this list to be useful. We need to be able to Create, Read, Update, and Destroy items in our checklist.

Lets add our first item to our checklist.py file that we created in section 00.

Add these 3 lines to checklist.py and run the file in the terminal as explained above.
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
* Line 2 Accesses a chunk of code within that object and passes in the value we wish to add to our list.
* Line 3 Prints the entire list to the console.
* Line 4 Accesses the append code within our list object and adds "World" to our list.
* Line 5 Prints the entire list again.

So now we have a list with two items: what's the proper way to access an item?
You can access individual items in the list by using the index where the data resides.
Indexes start at zero so to access the first element you will have to call on index 0 like this:

```python
checklist[0]
```
This will return

```
Hello
```

This line of code is simply accessing the first item in our list. Python lists will always start at 0 which may be a reason for some off by one errors that you may run into. Accessing the second item is as easy as calling `checklist[1]`. 

How about updating an item in the list?

Add the following line to the end of your script.

```python
checklist[1] = "Cats"
print(checklist)
```
The new line that is output in the terminal should be:

```
['Hello', 'Cats']
```
All this is doing is overwriting the data located in the second block of our list with the word "Cats."   

So that takes care of the first three letters, C, R, and U. Now we just the the last one - Destroy.

## Removing Items

We'll need to access different chunk of code -- known as a method -- inside our object. Enter the pop method.
Calling the pop method in our list will remove the last item in our list by default, unless of course we pass in the index of the item we want to remove.

```python
checklist.pop(1)
print(checklist)
```
This should output:
```
['Hello']
```

Now that we know how to CRUD our list we can start to make progress. There are also many more methods that you can access in this object as well as many different objects in Python. Check out the [python list documentation](https://docs.python.org/3/tutorial/datastructures.html) to see what other methods are available to you.


## Making our Code Reusable
Writing each command explicitly isn't a terribly useful way to program which is why you want to re-use your code as much as possible. Writing functions allows for this re-use and you'll find the majority of the code written in this tutorial will exist within functions.

A function is just a collection of code that allows for reuse and is declared as such:
```python
def my_fun_function(say_this):
    print(say_this)
```

This function when run will take an input and print it to the console. Every line below the function declaration ```def my_fun_function(say_this):``` must be indented to be included within that function. You can indent with spaces or tabs but once you choose one you can't mix the two.

Lets run our new function.

```
my_fun_function("Hello Worlds")
```

You'll see the output will be:

```
Hello Worlds
```

### Where do we go from here?

So we know that we're going to use a python list to keep our checklist in. We know how to CRUD our checklist -- so now lets make functions that we can call to make the process easier.

We'll need at least four functions.

### Create
We saw from above that we could create a new item in the list using the append method. So lets put that line inside this function.
```python
def create_item(item):
    checklist.append("Hello")
```

This won't work because it will just add ```Hello``` to every item. Lets update it a bit.

```python
def create_item(item):
    checklist.append(item)
```
And like magic you can add anything you want (within reason) to your list. Do you feel the power coursing through your fingers yet? No? Well just wait a bit then.

### Read
We found out above that we can access a list item using the index that corresponds to where it is in the list. This means we will need the index as a parameter that must be supplied when this function is called. 

So this function looks like this:
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

### Update

We saw from above that we can just assign a value to an index that already exists to update our list.

```python
checklist[1] = "Cats"
```

You can see by the hard coded values that we will need two parameters to make this re-usable. Otherwise, this is another two line function.

```python
def update(index, item):
    checklist[index] = item
```

### Destroy
The pop method was a handy way that allowed us to remove an item from our list. Lets see what it looks like inside a function

```python
def destroy(index):
    checklist.pop(index)
```

## Keep it Simple Stupid
When creating functions they should do as little as possible - a single thing if possible. They should be simple to read and understand. Anything that isn't immediately apparent should be noted with a comment in the code.

Comments are indicated with # and help not only yourself but anyone that comes after you.

## Testing
The code we wrote so far should be organized like this:
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

Testing code is so important that we won't cover it here much at all. However normally our testing code would reside in another file and be run with a testing tool like pytest. Using a tool like pytest allows you to automate the process of verifying that functions work. The process of testing is the same however instead of pytest interpreting the result, you will have to.

Test the functions you made by calling them with different values and checking the result.
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
This may be something we'll have to think about if we were going to implement this in production. If this function were called with an invalid index our program would crash and people would be sad. This is a topic for a stretch challenge or another tutorial however.

Remove the line that throws the error so we can move on.