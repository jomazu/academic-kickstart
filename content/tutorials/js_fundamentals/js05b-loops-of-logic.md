---
title: Loops continiued...
linktitle: JS Loops, ch-05b
toc: true
type: docs
date: "2017-12-04T00:00:00+01:00"
lastmod: "2017-12-05T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 8

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 8
---

## Requirements
The requirements for this chapter:  

- `.displayTodos` should **SHOW** `.todoText`  
- `.displayTodos` should **TELL YOU** if `.todos` is empty  
- `.displayTodos` should **SHOW** `.completed`  

In this section we will use `FOR LOOPS` to fix `.displayTodos` and make them work properly.  

## .displayTodos
We want the `.displayTodos` method to show the `.todoText` property.  

We have to do some processing on each object in our `.todos` array, and that is a perfect task for a `FOR LOOP`, because we want to repeat some code for every item in the array.  

Within Plunker add the following `FOR LOOP`:  

```javascript
for (var i = 0; i < this.todos.length; i++) {
  console.log(this.todos[i].todoText);
}
```

Before...  
```javascript
var todoList = {
  todos: [],
  displayTodos: function() {
    console.log(`My Todos: ${this.todos}`);
  },
```

After...  
```javascript
var todoList = {
  todos: [],
  displayTodos: function() {
    console.log('My Todos: '); // Removed ${this.todos}, not needed
    for (var i = 0; i < this.todos.length; i++) {
      console.log(this.todos[i].todoText);
    }
  },
```

Test, by running in the Chrome console:  
```javascript
// Automatically displays after adding
> todoList.addTodo('Product 1');
My Todos:
Product 1

> todoList.addTodo('Product 2');
My Todos:
Product 1
Product 2

// We can also run the displayTodos method separately
> todoList.displayTodos();
My Todos:
Product 1
Product 2
```

Recap...  

Note, we removed `${this.todos}` from the original `console.log` statement, because it was printing out objects to the console and was not very useful. Then we added a `FOR LOOP` to iterate through the todos array in the todoList object, and display the todoText for each index of the array.  


## .displayTodos (if empty)
We want `.displayTodos` to tell us if `.todos` is empty - i.e. no todos in the list.  

To do this, we will use an `if` / `else` statement to add **LOGIC** to our code.  

Example - logic:  
```javascript
if (condition) {
  // code that runs if condition is True
} else {
  // code that runs if condition is False
}


// if there are no todos
if this.todos.length === 0 
  console.log('Your todo list is empty!');
else
  print todos as normal (i.e. run displayTodos)
```

Example - code:  
```javascript
if (this.todos.length === 0) {
  console.log('Your Todo List is empty!');
} else {
  console.log('My Todos: ');
  for (var i = 0; i < this.todos.length; i++) {
    console.log(this.todos[i].todoText);
  }
}
```

So, this is how the code looked before any changes:  
```javascript
var todoList = {
  todos: [],
  displayTodos: function() {
    console.log('My Todos: ');
    for (var i = 0; i < this.todos.length; i++) {
      console.log(this.todos[i].todoText);
    }
  },
```

After implemented...  
```javascript
var todoList = {
  todos: [],
  displayTodos: function() {
    if (this.todos.length === 0) {
      console.log('Your TODO List is empty!');
    } else {
      console.log('My Todos: ');
      for (var i = 0; i < this.todos.length; i++) {
        console.log(this.todos[i].todoText);
      }
    }
  },
  addTodo: function(todoText) {
```

Test in Plunker:  
```javascript
> todoList.displayTodos();
Your TODO List is empty!

> todoList.addTodo('Test item added');
My Todos:
Test item added

> todoList.deleteTodo(0);
Your TODO List is empty!
```

## .displayTodos (show completed)
Recall, each todo object has a completed property that is a boolean. We want to have `.displayTodos` to show whether a todo has been completed or not.  

Example - logic:  
```javascript
( ) item 1 // not completed with (empty)
(x) item 2 // completed with (x)
(x) item 3 // completed with (x)
```

Example - code:  
```javascript
// Logical example
check if .completed is true
  print with (x)
else
  print with ( )

// Code block
if (this.todos[i].completed === true) {
  console.log('(x)', this.todos[i].todoText);
} else {
  console.log('( )', this.todos[i].todoText);
}
```

Before...  
```javascript
var todoList = {
  todos: [],
  displayTodos: function() {
    if (this.todos.length === 0) {
      console.log('Your TODO List is empty!');
    } else {
      console.log('My Todos: ');
      for (var i = 0; i < this.todos.length; i++) {
        // The following line will be removed in next step
        console.log(this.todos[i].todoText);
      }
    }
  },
  addTodo: function(todoText) {
```

After...  
```javascript
var todoList = {
  todos: [],
  displayTodos: function() {
    if (this.todos.length === 0) {
      console.log('Your TODO List is empty!');
    } else {
      console.log('My Todos: ');
      for (var i = 0; i < this.todos.length; i++) {
        if (this.todos[i].completed === true) {
          console.log('(x)', this.todos[i].todoText);
        } else {
          console.log('( )', this.todos[i].todoText);
        }
      }
    }
  },
  addTodo: function(todoText) {
```

Test in Plunker:  
```javascript
> todoList.displayTodos();
Your TODO List is empty!

> todoList.addTodo('item 1');
My Todos:
( ) item 1

> todoList.addTodo('item 2');
My Todos:
( ) item 1
( ) item 2

// Toggled
> todoList.toggleCompleted(1);
My Todos:
( ) item 1
(x) item 2

// Toggled again and now false
> todoList.toggleCompleted(1);
My Todos:
( ) item 1
( ) item 2
```
<br>
Recap...  
In this section we combined a `FOR LOOP` with `IF STATEMENTS` to add logic to the program.  
