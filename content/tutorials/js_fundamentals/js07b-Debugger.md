---
title: Debugger
linktitle: Debugger, ch-07b
toc: true
type: docs
date: "2017-12-10T00:00:00+01:00"
lastmod: "2017-12-10T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 12

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 12
---

## Using The Debugger (Step Through)
In this section we will learn how to use the **Debugger** and how to apply it to the code.  

For instance, to run the **debugger** on the `displayTodos` method in the `todoList` object, we must first insert a place for the program to **PAUSE** as it is running.  

In this case, we will insert `debugger;` on it's own line, as shown below...  
```javascript
// Before
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

// After
var todoList = {
  todos: [],
  displayTodos: function() {
    debugger;
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
```

To run the debugger, open Plunker and run the `script.js` file. Open the console, then call the method using: `todoList.displayTodos();`  

Now, you can use the `Step over next function call` be selecting the icon with a half circle (arrow head), and a dot underneath. This let's us see what is going on line-by-line.  

If you hover over the highlighted line, you can place your cursor over the values to actually see what they are.  

To jump out of the step function and back into normal execution mode, just select the `Resume script execution` icon with a right pointing arrow.  

Then, when finished with the `debugger`, simply remove `debugger;` from your code and save the file.  

## todoList.displayTodos
Run the **debugger** on the `displayTodos()` method, by running the program, and then calling the function from the console.  
- `todoList.displayTodos();`  
```javascript
displayTodos: function() {
    debugger;
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
```

## todoList.addTodo
Run the **debugger** on the `addTodo()` method, by running the program, and then calling the function from the console.  
- `todoList.addTodo('Running the debugger');`  
```javascript
addTodo: function(todoText) {
    debugger;
    this.todos.push({
      todoText: todoText,
      completed: false
    });
    this.displayTodos();
  },
```

## todoList.changeTodo
Run the **debugger** on the `changeTodo()` method, by running the program, and then calling the function from the console.  
- `todoList.addTodo('Change this item');`  
- `todoList.changeTodo(0, 'This item has been changed!');`  
```javascript
changeTodo: function(position, todoText) {
    debugger;
    this.todos[position].todoText = todoText;
    this.displayTodos();
  },
```

## todoList.deleteTodo
Run the **debugger** on the `deleteTodo()` method, by running the program, and then calling the function from the console.  
- `todoList.addTodo('Delete this junk!');`  
- `todoList.deleteTodo(0);`  
```javascript
deleteTodo: function(position) {
    debugger;
    this.todos.splice(position, 1);
    this.displayTodos();
  },
```

## todoList.toggleCompleted
Run the **debugger** on the `toggleCompleted()` method, by running the program, and then calling the function from the console.  
- `todoList.addTodo('Toggle this');`  
- `todoList.toggleCompleted(0);`  
```javascript
toggleCompleted: function(position) {
    debugger;
    var todo = this.todos[position];
    todo.completed = !todo.completed;
    this.displayTodos();
  },
```

## todoList.toggleAll
Run the **debugger** on the `toggleAll()` method, by running the program, and then calling the function from the console. - `todoList.addTodo('This is true');`  
- `todoList.toggleCompleted(0);`  
- `todoList.toggleAll();`  
```javascript
toggleAll: function() {
    debugger;
    var totalTodos = this.todos.length;
    var completedTodos = 0;
    for (var i = 0; i < totalTodos; i++) {
      if (this.todos[i].completed === true) {
        completedTodos++;
      }
    }
    if (completedTodos === totalTodos) {
      for (var i = 0; i < totalTodos; i++) {
        this.todos[i].completed = false;
      }
    } else {
      for (var i = 0; i < totalTodos; i++) {
        this.todos[i].completed = true;
      }
    }
    this.displayTodos();
  }
```

## Use the Debugger all the time
The debugger is one of the most important weapons that you have at your disposal when programming.  

1) It helps you solve problems if you have an issue.  
2) Helps you to understand your code and how it works under the hood.  
3) Use it all the time and get good at using it, so that it becomes second nature.  
4) You no longer need to wonder what is happening, by using the debugger you can see what is happening.  

## Focus on Understanding
Focus on understanding, stop worrying about building from scratch. Use the Debugger and ask questions on [Stack Overflow](https://stackoverflow.com/questions/tagged/javascript).  
   