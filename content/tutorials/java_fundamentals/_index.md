---
# Course title, summary, and position.
linktitle: Java Fundamentals
summary: Getting Started with Java.
weight: 4

# Page metadata.
title: Overview
date: "2019-11-21"
lastmod: "2020-07-05"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  java_fundamentals:
    name: Overview
    weight: 4
---

---
🕮 [**TOC**]({{< ref "/toc.md" >}}) 

![Java logo](https://res.cloudinary.com/jomazu/image/upload/w_0.4,c_scale/v1574364405/jomazu/logos/java_logo.png)

<br>

---
<br>

The Java Programming Language is a gerneral-purpose, concurrent, strongly-typed, class-based object-oriented language. It is normally compiled to the bytecode instruction set and binary format defined in the Java Virtual Machine Specification.

<br>

---
<br>

## What is a Computer Program?
A Computer Program is a List of Instructions given to a computer on how to perform a given task.

<br>

---
<br>

## What are Methods?
[Methods](https://www.geeksforgeeks.org/methods-in-java/) are Named Blocks of Instructions. For instance, a List of Instructions for changing a tire can be broken down into four (4) Named Blocks of Intructions (Methods):

1. Park Car
2. Get Tools
3. Change Tire
4. Return Tools

Each Method contains specific steps (details) for completing a task. These details are wrapped in the Method. Thus, Methods are used to organize a long list of instructions in a Computer Program into manageable Blocks. Methods are used to achieve code reusability - write a method once and use it many times.

The starting point in every Java Program is the **Main Method**, which is where you would **Call** your Methods. For example, in the changing a tire program, the Methods for Park Car, Get Tools, Change Tire, or Return Tools would be **Called** within the **Main Method**. A Method is a container of Instructions.

```java
main()
```

```java
class Example{  
    public static void main(String args[]){  
     System.out.println("Hello, Jomazu!");  
    }  
}  
```

<br>

---
<br>

## What is a Class?
A [Class](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) is a place where you define your Methods, it is a container of Methods. A Class is a user-defined blueprint that has a set of attributes and behaviors  that define the object they are supposed to represent.

* **Attributes** (Properties) are variables that will hold a particular value within a class.
* **Behaviors** (Methods) are functions that are related to a class.
* **Instance** is an object created from a class blueprint.
* **Constructor** is a special method (i.e. function) or behavior inside every class that creates and initializes instances.
  * The constructor may or may not take inputs. The name of the constructor is always the same name as the Class.
  * The `this` keyword and the `dot` operator is used to access the attribute variable for an object you are constructing. The `this` keyword helps Java make a distinction between the attribute variable and the parameter variable.
  * A constructor is called like any other function. The only difference is that because you are creating a new instance, you have to use the `new` keyword.

<br>

---
<br>

## Instance Methods vs. Class Methods

* **Instance Methods** are also referred to as (non-static) methods since you need an instance to use them. 

> Example:
> ```java
> String studentFirstName = "Kayla";
> System.out.println(studentFirstName.charAt(1));
> ```
> ```terminal
> > a
> ```
> Since the `.charAt()` method is accessed through a **String instance**, it is an **instance** (non-static) method instead of a **class** (static) method.

* **Class Methods** are referred to as (static) methods because you do not need an instance to use them.

<br>

---
<br>

## What is a Package?
A [Package](https://docs.oracle.com/javase/tutorial/java/concepts/package.html) is a namespace that organizes a set of related classes and interfaces. Conceptually you can think of packages as being similar to different folders on your computer. You might keep HTML pages in one folder, images in another, and scripts or applications in yet another. Because software written in the Java programming language can be composed of hundreds or thousands of individual classes, it makes sense to keep things organized by placing related classes and interfaces into packages.