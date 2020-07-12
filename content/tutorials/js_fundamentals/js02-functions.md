---
title: Functions
linktitle: JS Functions, ch-02
toc: true
type: docs
date: "2017-12-04T00:00:00+01:00"
lastmod: "2017-12-04T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

Functions are just recipes. Generally speaking, a function is a code snippet (subprogram) that can be called by other code, by itself, or a variable that refers to the function.  

When a function is called, arguments are passed to the function as input, and the function can optionally return an output.  

Using a recipe analogy, this would be the basic concept of a function to make a salami sandwich...  

```javascript
// The steps
makeSalamiSandwich
  Get one slice of bread.
  Add salami.
  Put a slice of bread on top.

// The function
  function makeSalamiSandwich() {
    Get one slice of bread;
    Add salami;
    Put a slice of bread on top;
  }

// Call the function
makeSalamiSandwich();
```

## Customizing Functions
- [Parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function) - the names of the arguments to be passed to the function.  

Using the same recipe analogy from above, we will adjust the steps to accomodate for customizing the Salami sandwich:  

```javascript
// The steps
makeSandwichWith ____
  Get one slice of bread.
  Add ____.
  Put a slice of bread on top.

// The function
  function makeSandwichWith(filling) {
    Get one slice of bread;
    Add filling;
    Put a slice of bread on top;
  }

// Call the function
makeSandwichWith(salami);
```

Conceptual example of customizing a function:  
```javascript
> function sayHiTo(person) {
  console.log(`Hi, ${person}`);
}

// Set the person variable to John
> sayHiTo('John');
Hi, John
```
