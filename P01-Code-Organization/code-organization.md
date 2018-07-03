---
title: Organizing the Project
slug: organization
---
# 01 Organizing the Code
> Beautiful is better than ugly.
> 
> Explicit is better than implicit.
> 
> Simple is better than complex.
> 
> Complex is better than complicated.
> 
> --Tim Peters (The Zen of Python)

When you construct a building, you don't start by digging a hole in the ground, you start by drawing up plans. The same should be true when you're writing software as well. Code can be a challenge to read unless it's well organized and properly commented. By creating a plan of action you can organize and prioritize the most important features of your project and allow for greater maintainability over the long run. 

## Agile Development
How a person or an organization decides to develop a piece of software will vary wildly on who's in charge. **Agile development** is a common methodology that allows for a project to rapidly improve by constant iteration instead of the alternative **waterfall** approach that would have an entire project built to perfection before being released. Agile development is a whole topic by itself but a useful tool we can take from it is the concept of **user stories**. 

## User Stories
By focusing on our desired results, we are more likely to stay on track with the features that we need instead of creating features for the sake of having features. Lets try some user stories here to get a hang of it.

An easy way to start using stories is to frame it in a template. You have a user that desires a feature so that they can do something.

An easy template is shown here.

As **[a user]**, I want **[some feature]** so that I can **[do something]**.

In our case our user stories will look like this:

As **Captain Rainbow** I want to **be able to access a checklist from the terminal** so that I can **easily run it anywhere that has bash**.

As **Captain Rainbow**, I want to **be able to add to a list all the colors I need to wear in a day** so I can **remember which colors I need to wear**.

As **Captain Rainbow**, I want to **be able to mark off colors that I have already chosen for the day** so I can **know that it's already represented**.

As **Captain Rainbow**, I want to **be able to remove items from the list** so I can **remove duplicates**.

As **Captain Rainbow**, I want to **be able to update items in the list** so I can **fix any errors**.

As **Captain Rainbow**, I want to **be able to see everything in my list at once** so I can **know what is in it**.

## Creating a Plan
So from our user stories we can generate a list of important features and functionalities that our users will expect from our application.

This list of features tells me that Captain Rainbow needs to be able to create, read, update, and destroy items in a list.
We will additionally need to be able to see every item in the list, and mark off items he's already wearing.

To further simplify matters we can say each of these features can be written as a function that can be called whenever we want to do that specific action.

Now we're starting to have a good picture of what we need.

1. A list resource.
2. CRUD functions for the list resource.
3. Helper functions to view list and mark items as worn.

## PEP8 Style Guide
```
A Foolish Consistency is the Hobgoblin of Little Minds
    -- Python Developers Guide
```

The PEP8 style guide reminds us that "[o]ne of Guido's key insights is that code is read much more often than it is written." Guido Van Rossum, also known as the "Benevolent Dictator for Life", created and still oversees the development of the Python language.

It is this concept, that consistent code is easier to read, that lies behind the Python style guide. When writing code in Python always try to conform with the styleguide's specifications. Mainly this means using snake case instead of camel case ( snake_case vs CamelCase ). If you need to reference the guide it's [available online](https://www.python.org/dev/peps/pep-0008/).
