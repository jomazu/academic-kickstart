---
title: Booleans
linktitle: JS Booleans, ch-04
toc: true
type: docs
date: "2017-12-04T00:00:00+01:00"
lastmod: "2017-12-04T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 6

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 6
---

## Requirements
The requirements for this chapter:  

- `todoList.addTodo` should **ADD** objects  
- `todoList.changeTodo` should **CHANGE** the `todoText` property  
- `todoList.toggleCompleted` should **CHANGE** the completed property  

This section will also cover **Booleans**, which is a representation of true or false.  

## todoList.addTodo
Right now we are adding `todos` as text. We are going to change this, so that `addTodo` will add **objects**, instead of text to our todo array.  

Using objects instead of text (i.e. item 1 etc.) in our array will give us the ability to represent more complicated data.  

This is an example of the object structure we will use to replace the current todos array:  

```javascript
{
  todoText: 'item 1',
  completed: false // Boolean true or false
}
```

Go to Plunker and open the `script.js` file in the `PJS-V3` plunk, where we will make the following changes:  

Before...  
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
```

After...  
```javascript
var todoList = {
  todos: [],  // Removed original item contents
  displayTodos: function() {
    console.log(`My Todos: ${this.todos}`);
  },
  addTodo: function(todoText) { // Changed todo to todoText
    this.todos.push({ // Changed from todo paramater to todoText object
      todoText: todoText // todoText property name (left) and todoText parameter
      completed: false // completed property name (left) and oolean default to false
    });
    this.displayTodos();
  },
```

Test the new todos object in Plunker:  
```javascript
> todoList.displayTodos();
My Todos:

> todoList.addTodo('new todo item');
My Todos: [object Object]

> todoList.todos;
[ { todoText: 'new todo item', completed: false } ]
```

## todoList.changeTodo
Now, we need to modify the `changeTodo` method, so that it changes just the `todoText` property on each todo object.  

Remember, the `addTodo` method now adds objects to our array, and those objects have two properties (todoText and completed).  

Go to Plunker and open the `script.js` file in the `PJS-V3` plunk and make the following changes:  

Before...  
```javascript
changeTodo: function(position, newValue) {
    this.todos[position] = newValue;
    this.displayTodos();
  },
```

After...  
```javascript
changeTodo: function(position, todoText) { // Change newValue to todoText
    this.todos[position].todoText = todoText;
    this.displayTodos();
  },
```

Test the modified `changeTodo` method in Plunker:  
```javascript
> todoList.todos;
[ { todoText: 'new todo item', completed: false } ]

> todoList.changeTodo(0, 'changed todo item');
My Todos: [object Object]

> todoList.todos;
[ { todoText: 'changed todo item', completed: false } ]
```

## todoList.toggleCompleted
Now, we need to add a method called `toggleCompleted` that changes the value of the completed property, which is a boolean value (true or false).  

Aside example of a boolean variable:  
```javascript
> var johnBoolean = false;

> johnBoolean
false

> !johnBoolean
true

// Flipped (using the ! bang operator)
// The original value of the variable is now true
> johnBoolean = !johnBoolean 

> johnBoolean
true
```

This is a brand new method, so there is no before snapshot.  
```javascript
toggleCompleted: function(position) {
  var todo = this.todos[position];
  todo.completed = !todo.completed;
}
```

Now, our `script.js` file should mirror the following:  
```javascript
var todoList = {
  todos: [],
  displayTodos: function() {
    console.log(`My Todos: ${this.todos}`);
  },
  addTodo: function(todoText) {
    this.todos.push({
      todoText: todoText,
      completed: false
    });
    this.displayTodos();
  },
  changeTodo: function(position, todoText) {
    this.todos[position].todoText = todoText;
    this.displayTodos();
  },
  deleteTodo: function(position) {
    this.todos.splice(position, 1);
    this.displayTodos();
  },
  toggleCompleted: function(position) {
    var todo = this.todos[position];
    todo.completed = !todo.completed;
    this.displayTodos();
  }
};
```

Test the new `toggleCompleted` method in Plunker:  
```javascript
> todoList.addTodo('1st todo item');
My Todos: [object Object]

> todoList.addTodo('2nd todo item');
My Todos: [object Object],[object Object]

> todoList.todos;
[ { todoText: '1st todo item', completed: false },
  { todoText: '2nd todo item', completed: false } ]

// Changed index 1 to completed
> todoList.toggleCompleted(1);

> todoList.todos;
[ { todoText: '1st todo item', completed: false },
  { todoText: '2nd todo item', completed: true } ]
```

## Review
We changed the structure of the array to be an array of objects, rather than an array of just text.  

We modified our `changeTodo` method so that it only changes the todo text properties on each todo object.  

We learned about booleans and how to take the opposite of a boolean value in our `toggleCompleted` method.  
 