---
title: Refactoring
linktitle: Refactoring, ch-08
toc: true
type: docs
date: "2017-12-10T00:00:00+01:00"
lastmod: "2017-12-10T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 13

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 13
---

## Refactoring
Code refactoring is the process of restructuring existing computer code without changing its external behavior.  

The key with refactoring is that it improves non-functional attributes of the software.  

For instance, refactoring makes your code...  

- More readable  
- A little easier to understand  
- Neater in appearance  

## Refactoring the Buttons
First, review the original way that we created and called our button methods.  

Previous HTML code...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <button id="displayTodosButton">Display Todos</button>
    <button id="toggleAllButton">Toggle All</button>
    
    <script src="script.js"></script>
  </body>

</html>
```

Previous JS code...  
```javascript
var displayTodosButton = document.getElementById('displayTodosButton');
var toggleAllButton = document.getElementById('toggleAllButton');

displayTodosButton.addEventListener('click', function() {
  todoList.displayTodos();
});

toggleAllButton.addEventListener('click', function() {
  todoList.toggleAll();
});
```

Now, take a look at how we **REFACTORED** the code to make it follow the principles or **DRY** (Don't Repeat Yourself).  

Also, note that we created a new **object** called `handlers` in `script.js`, because we wan't the **methods** on this new object to **handle** different **EVENTS**.  

For example, when you **click** on this **BUTTON**, we wan't something to **handle** that **event**.  

Refactored HTML code...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <button onclick="handlers.displayTodos()">Display Todos</button>
    <button onclick="handlers.toggleAll()">Toggle All</button>
    
    <script src="script.js"></script>
  </body>

</html>
```

Refactored JS code...  
```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  toggleAll: function() {
    todoList.toggleAll();
  }
};

```
