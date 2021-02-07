---
title: Captain Rainbow's Color Checklist
slug: installation
---
## Captain Rainbow's Color Checklist

![](the-truth-about-rainbows.jpg)

The power of a single color is dwarfed in comparison by the power of many colors together. Captain Rainbow has a lot of important tasks on his plate and all of them must be done or the world will suffer. Leaving a color out of his wardrobe would only lessen his ability to vanquish the ills of the world.

There is at least one way to make sure that he never leaves home without a given hue -- a satisfying checklist.

By beginning his day with a simple checklist he can prepare for what the rest of the day will throw at him.

We are going to write a Python program that helps Captain Rainbow decide what he is going to wear. Everyday he has to decide what color each of his clothing items will be. While this is a fun task on the weekends, it can be extra challenging during the week when he is trying to get to work on time.

**Some things to consider:**

1. There are seven colors in the rainbow, and seven items of clothing to color.<br>
2. He can never wear the same color on any of his items. If he is wearing a purple shoe, he cannot wear a second purple shoe.<br>
3. He must wear every color of the rainbow each day.<br>

Can you help make his mornings easier by developing an algorhythm that will make it easier to pick his clothes?

## What you'll need.

* A computer with Python 3 installed
* Access to a terminal that runs Bash

This tutorial assumes that you're using a computer running any version of Mac OS X. Other operating systems may require a dramatically different setup which is beyond the scope of this tutorial.

You can use the terminal to check which version of python you're using.

* Click on the Finder icon in the Dock
* In the Go menu click Applications
* Search inside the Applications folder for Terminal or iTerm2
* Double click the terminal to open it

At the terminal prompt type
```
$ python --version
```

Some systems may have python2 and python3 installed. If you saw python version 2.x then you may have to specify the use of version 3 by using the following command.

```
$ python3 --version
```

This tutorial requires Python version 3 to run. If you had to run the second command to specify version 3 then instead of running ```python ./myfilename.py``` you'll want to run ```python3 ./myfilename.py``` to execute the python script you're going to write.

##  Getting Started
To begin with we'll create a directory for the project to live in. Use the `mkdir` command to do this.
In the terminal enter

```
$ mkdir checklist
```

You can verify that a new folder was created by typing

```
$ ls
```

The terminal will list all files and folders in the directory you're currently in including the one you just created. Enter the directory you made by using the cd command.

```
$ cd checklist
```

Now if you use the `ls` command you'll see that the directory is empty. Use ```touch``` to create our new file.

```
$ touch checklist.py
```
You should be able to verify that a new empty file was created named checklist.py

## Choose an Editor

There are many to choose from and each has their following. Popular choices include Atom, Sublime Text, Visual Studio Code, and for the more adventurous souls VIM. This tutorial will remain editor agnostic so choose the one that is the most comfortable for you.

## A Note About The Atom Text Editor and Flake8
If you are using Atom you may come across an error regarding the flake8 linter. A linter just goes through and verifies that your code has the proper formatting and syntax and is very helpful when it works. For some reason however Atom comes with a deprecated linter that fails to work with Python. You will want to go into the Atom menu and choose `Preferences...`.

Click on `Packages` and search for flake8.

You'll want to disable or uninstall the flake8 package to get rid of the errors that show up.


## Write Your First Line of Python

Open `checklist.py` in your chosen text editor and write the following line of code.

```python
print("Hello World")
```
Save the file and in your terminal run the following command.

```
$ python ./checklist.py
```

You should see the following in the terminal.

```
Hello World
```

## Testing Things Out
Sometimes you may want to run a few lines of code separately just to explore the language. Python includes a handy mode that allows you to run commands on the fly.

Typing `python` in the terminal window will open the python interpreter in interactive mode.

You may find it helpful to test some code in interactive mode and verify it works before putting it in a project.

When you want to exit interactive mode call the exit function by typing `exit()` or hit ctl-d keys on the keyboard.
