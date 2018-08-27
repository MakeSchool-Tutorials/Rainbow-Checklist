---
title: Organizing the Project
slug: organization
---
## Organizing the Code
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
By focusing on our desired results, we're more likely to stay on track with the features that we need instead of creating features for the sake of having features. Lets try some user stories here to get a hang of how they work.

An easy way to write user stories is to frame them in a loose template. You have a user that desires a feature so that they can do something.

**As [a type of user], I want [some feature] so that I can [do something].**

With user stories you want to approach a problem from the perspective of the user. Different types of users will have different experiences with the application. Here we only have one type of user in mind so we won't have to worry about what different types of users will or won't be able to see.

In our case our user stories will look something like this:

* As a user, I want to be able to create, read, update, and destroy items in a checklist.

* As a user, I want to be able to mark off colors so I can know that it's already represented.

* As a user, I want to be able to see everything in my list at once so I know what is in my list.

So from our user stories we can generate a list of important features and functionalities that our users will expect from our application.

## CRUD
Our first user story relates to the four fundamental operations that are needed for even the simplest operability. These functions -- **create**, **read**, **update**, and **destroy** -- are generally necessary for any software to be considered complete.  

These four functions are so fundamental that they're often referred to by the acronym **CRUD**.

By simply making sure that our list includes these four operations we can be sure that at the very least our most basic operations can be met. Though we will need some more tools in additions to these four here.

## PEP8 Style Guide
```
A Foolish Consistency is the Hobgoblin of Little Minds
    -- Python Developers Guide
```

The PEP8 style guide reminds us that "[o]ne of Guido's key insights is that code is read much more often than it is written." Guido Van Rossum, also known as the "Benevolent Dictator for Life", created and still oversees the development of the Python language.

It is this concept, that consistent code is easier to read, that lies behind the Python style guide. When writing code in Python always try to conform with the styleguide's specifications. Mainly this means using snake case instead of camel case ( snake_case vs CamelCase ). If you need to reference the guide it's [available online](https://www.python.org/dev/peps/pep-0008/).
