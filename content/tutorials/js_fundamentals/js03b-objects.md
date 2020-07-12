---
title: Objects continued...
linktitle: JS Objects, ch-03b
toc: true
type: docs
date: "2017-12-04T00:00:00+01:00"
lastmod: "2017-12-04T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 5

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 5
---

## Requirements
The requirements for this chapter:

- It should **STORE** the todos array on an object  

*Place the following methods on an object that represents a Todo list*   

- It should have a **displayTodos** method   
- It should have an **addTodo** method  
- It should have a **changeTodo** method  
- It should have a **deleteTodo** method  

This helps to organize our code and ensure that everthing related to a Todo list is on a Todo list object. 

## STORE
**STORE** the `todos array` on an `object`.  

Go to Plunker and open `PJS - V3` and select `script.js`...  

Enter the following:  
```javascript
var todoList = {
  todos: ['item 1', 'item 2', 'item 3']
};
```

- `save` on Plunker  
- `run` on Plunker  
- Right-click and click inspect  
- Open the `console` tab and select the `top` dropdown and select `plunkerPreviewTarget`  

Now, you can access the Plunker data inside of your `PJS - V3` program.  

## displayTodos
Change the `displayTodos` function from a standalone function to a method on our `todoList` object.  

Previously created standalone function shown for context only:  
```javascript
function displayTodos() {
  console.log(`My Todos: ${todos}`);
}
```

Within Plunker, add the new `displayTodos Method` (anonymous function) to the `todoList` object:  
```javascript
displayTodos: function() {
  console.log(`My Todos: ${this.todos}`);
}
```

The `todoList` object should now look like such...  
```javascript
var todoList = {
  todos: ['item 1', 'item 2', 'item 3'],
  displayTodos: function() {
    console.log(`My Todos: ${this.todos}`);
  }
};

> todoList.displayTodos();
My Todos: item 1,item 2,item 3
```

## addTodo
Change the `addTodo` function from a standalone function to a method on our `todoList` object.  

Previously created standalone function shown for context only:  
```javascript
function addTodo(todo) {
  todos.push(todo);
  displayTodos();
}
```

Within Plunker, add the new `addTodo Method` (anonymous function) to the `todoList` object:  
```javascript
addTodo: function(todo) {
  this.todos.push(todo);
  this.displayTodos();
}
```

The `todoList` object should now look like such...  
```javascript
var todoList = {
  todos: ['item 1', 'item 2', 'item 3'],
  displayTodos: function() {
    console.log(`My Todos: ${this.todos}`);
  },
  addTodo: function(todo) {
    this.todos.push(todo);
    this.displayTodos();
  }
};

> todoList.displayTodos();
My Todos: item 1,item 2,item 3

> todoList.addTodo('item 4');
My Todos: item 1,item 2,item 3,item 4
```

## changeTodo
Change the `changeTodo` function from a standalone function to a method on our `todoList` object.  

Previously created standalone function shown for context only:  
```javascript
function changeTodo(position, newValue) {
  todos[position] = newValue;
  displayTodos();
}
```

Within Plunker, add the new `changeTodo Method` (anonymous function) to the `todoList` object:  
```javascript
changeTodo: function(position, newValue) {
  this.todos[position] = newValue;
  this.displayTodos();
}
```

The `todoList` object should now look like such...  
```javascript
var todoList = {
  todos: ['item 1', 'item 2', 'item 3'],
  displayTodos: function() {
    console.log(`My Todos: ${this.todos}`);
  },
  addTodo: function(todo) {
    this.todos.push(todo);
    this.displayTodos();
  },
  changeTodo: function(position, newValue) {
    this.todos[position] = newValue;
    this.displayTodos();
  }
};

> todoList.changeTodo(0, 'plunker');
My Todos: plunker,item 2,item 3
```

## deleteTodo
Change the `deleteTodo` function from a standalone function to a method on our `todoList` object.  

Previously created standalone function shown for context only:  
```javascript
function deleteTodo(position) {
  todos.splice(position, 1);
  displayTodos();
}
```

Within Plunker, add the new `deleteTodo Method` (anonymous function) to the `todoList` object:  
```javascript
deleteTodo: function(position) {
  this.todos.splice(position, 1);
  this.displayTodos();
}
```

The `todoList` object should now look like such...  
```javascript
var todoList = {
  todos: ['item 1', 'item 2', 'item 3'],
  displayTodos: function() {
    console.log(`My Todos: ${this.todos}`);
  },
  addTodo: function(todo) {
    this.todos.push(todo);
    this.displayTodos();
  },
  changeTodo: function(position, newValue) {
    this.todos[position] = newValue;
    this.displayTodos();
  },
  deleteTodo: function(position) {
    this.todos.splice(position, 1);
    this.displayTodos();
  }
};

> todoList.deleteTodo(0);
My Todos: item 2,item 3
```
