---
title: Arrays
linktitle: JS Arrays, ch-01
toc: true
type: docs
date: "2017-12-04T00:00:00+01:00"
lastmod: "2017-12-04T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

An array (list) is an ordered collection of data, used to store multiple values in a single variable. In the JavaScript language, arrays are considered objects. Objects have properties and methods:  

* **Properties** - pieces of meta information about an object that can be retrieved and used.  
* **Methods** - functions that belong to an object.  

## Requirements
Arrays needed for building a `TODO` application:  

- [x] It should have a place to **STORE** todos  
- [x] It should have a way to **DISPLAY** todos  
- [x] It should have a way to **ADD** new todos  
- [x] It should have a way to **CHANGE** a todo  
- [x] It should have a way to **DELETE** a todo  

## STORE
Create a place to **STORE** todos.  

- [array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) (list) - used to **STORE** todos.   

Example:  
```javascript
> var todos = ['item 1', 'item 2', 'item 3'];
```

## DISPLAY
Create a way to **DISPLAY** todos.  

- [console.log](https://developer.mozilla.org/en-US/docs/Web/API/Console/log) - the function used to **DISPLAY** todos. This method allows multiple arguments.  
- [about:blank](https://www.lifewire.com/about-blank-4125143) - open a new browser tab and type `about:blank` to view a blank web page. A better option is to set it as your homepage.  
- [option + command + i](https://support.apple.com/en-us/HT201236) - shows or hides the inspector/developer tools window.  

Example:  
```javascript
> var todos = ['item 1', 'item 2', 'item 3'];

> console.log(todos);
["item 1", "item 2", "item 3"]

// Pass in the text (argument): My Todos
> console.log('My Todos:', todos);
My Todos: [ 'item 1', 'item 2', 'item 3' ]
```

## ADD
Create a way to **ADD** todos.  

- [push](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) - the method used to **ADD** todos to the end of the list (array).  

Example:  
```javascript
> todos.push('item 4');
4

> console.log('My Todos:', todos);
["item 1", "item 2", "item 3", "item 4"]
```

## CHANGE
Create a way to **CHANGE** todos.  

First, access (**index** into) an array item, then **CHANGE** it's value.  

- [index](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) - used to access an array item.  

Example:  
```javascript
> console.log('My Todos:', todos);
["item 1", "item 2", "item 3", "item 4", "item 5"]

> todos[2];
"item 3"

// Alternate method to find the index of an item
> todos.indexOf('item 3');
2

// Change item at index[0]
> todos[0] = 'item 1 updated';
"item 1 updated"

> console.log('My Todos:', todos);
["item 1 updated", "item 2", "item 3", "item 4", "item 5"]

// Change item at index[4]
> todos[4] = 'item 5 updated';
"item 5 updated"

> console.log('My Todos:', todos);
["item 1 updated", "item 2", "item 3", "item 4", "item 5 updated"]
```

## DELETE
Create a way to **DELETE** todos.  

- [splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) - the method used to **DELETE** todos.  

Example:  
```javascript
> todos;
["item 1 updated", "item 2", "item 3", "item 4", "item 5"]

// Remove 1 item at index position 0
> todos.splice(0, 1);
["item 1 updated"]

> todos;
["item 2", "item 3", "item 4", "item 5"]

// Remove 1 item at index position 3
> todos.splice(3, 1);
["item 5"]

> todos;
["item 2", "item 3", "item 4"]

// Remove 2 items at index position 1
> todos.splice(1, 2);
["item 3", "item 4"]

> todos;
["item 2"]
```
