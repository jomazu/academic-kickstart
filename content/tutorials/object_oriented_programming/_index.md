---
# Course title, summary, and position.
linktitle: Object Oriented Programming
summary: The basics of Object Oriented Programming (OOP).
weight: 6

# Page metadata.
title: Overview
date: "2016-06-04T00:00:00Z"
lastmod: "2016-06-04T00:00:00Z"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  object_oriented_programming:
    name: Overview
    weight: 6
---

Object-oriented programming (OOP) is the foundation of modern programming languages and it's fundamental unit is the **object**. Around since the early 1960s, it did not start to gain momentum until the mid to late 1990s. Nonetheless, object-oriented languages are defined by the following three terms:

- `Encapsulation`
- `Inheritance`
- `Polymorphism`


## What is an object?
When you look at a person, you see the person as an object. And an object is defined by two components:  

- [x] Attributes (Properties) - eye color, age, and height etc.
- [x] Behaviors (Methods) - walking, talking, and breathing etc.  

In object-oriented design, **both** properties and methods are contained within a single object. Objects are the building blocks of an object-oriented program.  

##### *What is an object-oriented language?*
<iframe width="280" height="158" src="https://www.youtube.com/embed/SS-9y0H3Si8" frameborder="0" allowfullscreen></iframe>  

## Encapsulation

By combining the properties and methods in the same object, we have what is called **encapsulation**, which allows us to control access to the data in the object.  

- **Property** = data
- **Method** = behavior
- **Object** = entity
- **Class** = template for an object (blueprint)

In general, two objects communicate with each other via their methods. Keep in mind that objects should not manipulate the internal data of other objects. It is best to build small objects with specific tasks versus building large objects that perform many.  

* The restriction of access to certain attributes and/or methods is called **data hiding**. For this to work, all attributes should be declared as *private*.
* Objects are also known as **instances**. For example, a circle object is an instance of the circle class. In other words, a class is used to create an object. Thus, an object cannot be instantiated without a class!  

## Inheritance

**Inheritance** allows a class to inherit the properties and methods of another class. This allows the creation of brand-new classes by abstracting out common attributes and behaviors.  

## Polymorphism

Polymorphism is a Greek word that literally means many shapes. In object-oriented programming, we can use the same method, the same name, and same arguments to cause different things to happen according to the class in which we invoke a method. This feature is known as **polymorphism**.  
