---
title: HTML and The DOM
linktitle: HTML, ch-07
toc: true
type: docs
date: "2017-12-10T00:00:00+01:00"
lastmod: "2017-12-10T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 11

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 11
---

## Requirements
The requirements for this chapter:  

- There should be a "Display todos" **BUTTON** and a "Toggle all" **BUTTON** in the app.  
- Clicking "Display todos" should run `todoList.displayTodos();`  
- Clicking "Toggle all" should run `todoList.toggleAll();`  

## HTML
Hyper-Text Markup Language ([HTML](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics)) is a language programmer's use for describing web pages.  

HTML is not a programming language; it is a markup language that defines the structure of your content. HTML consists of a series of elements, which you use to enclose, or wrap, different parts of the content to make it appear a certain way, or act a certain way.  

- ***html*** *element* - the content between opening `<html>` and closing `</html>` tags.  
- ***head*** *element* - the content between opening `<head>` and closing `</head>` tags.  
- ***body*** *element* - the content between opening `<body>` and closing `</body>` tags. This is what visually appears on a web page.  

In Plunker, open `index.html` to see the following HTML example:  
```html
<!DOCTYPE html>

<!-- html element (parent) -->
<html>

  <!-- head element (child to html parent) -->
  <head>
    <!-- link element (child to head element) -->
    <link rel="stylesheet" href="style.css">
    <!-- script element (child to head element) -->
    <script src="script.js"></script>
  </head>

  <!-- body element (child to html parent) -->
  <body>
    <!-- h1 element (child to body element) -->
    <h1>Hello Plunker</h1>
  </body>

</html>
```

## Document Object Model
The Document Object Model ([DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)) connects web pages to scripts or programming languages - usually JavaScript. The DOM model represents a document with a logical tree. Each branch of the tree ends in a node, and each node contains objects. DOM methods allow programmatic access to the tree; with them you can change the document's structure, style or content. Nodes can have event handlers attached to them. Once an event is triggered, the event handlers get executed.  

In laymans terms, the DOM is your browser's interpretation of your HTML.  

- `document` - represents the DOM.  

## Button
In this section we will begin creating a UI for user's to interact with - something that they can click on (i.e. **BUTTONS**) and/or type into right on the page, without having to use the console.  

`index.html` before...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
    <script src="script.js"></script>
  </head>

  <body>
    <h1>Todo List</h1>
  </body>

</html>
```

`index.html` after...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
    <script src="script.js"></script>
  </head>

  <body>
    <h1>Todo List</h1>
    
    <button>Display Todos</button>
    <button>Toggle All</button>

  </body>

</html>
```

## Display Todos
In this section, we want to:  
1) Get access to the display todos button.  
2) Run the displayTodos method, when someone clicks the 'Display Todos' button.  

In Plunker, open `script.js`. This is the file we will use to wire-up our buttons.  

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
        if (this.todos[i].completed === true) {
          console.log('(x)', this.todos[i].todoText);
        } else {
          console.log('( )', this.todos[i].todoText);
        }
      }
    }
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
  },
  toggleAll: function() {
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
};

```

Remember, `document` represents the DOM. The `document` object has methods on it that allow you to `select` a specific `element`.  

For instance, add an `attribute` to an element tag, so that we can `id` it from our JavaScript file. Once an HTML element tag has been given an `id`, we can call a method from our JS file to access it.  

An attriubute, simply gives an element additional information.  
- [id](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/id) - The id **global attribute** defines a unique identifier (ID) which must be unique in the whole document. Its purpose is to identify the element when linking (using a fragment identifier), scripting, or styling (with CSS).  
- [rel](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes) - Specifies the relationship of the target object to the link object.  
- [href](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes) - The URL of a linked resource.   
- [src](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes) - The URL of the embeddable content.  
  
```html
<!-- Before -->
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
    <script src="script.js"></script>
  </head>

  <body>
    <h1>Todo List</h1>
    
    <button>Display Todos</button>
    <button>Toggle All</button>
    
  </body>

</html>


<!-- After -->
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <button id="displayTodosButton">Display Todos</button>
    <button>Toggle All</button>
    
    <!--
    Moved the script tag right above the closing body tag.
    This will ensure that the script.js file runs AFTER
    the HTML in index.html is parsed.
    --> 
    <script src="script.js"></script>
  </body>

</html>
``` 

Methods to `getElementById()` and `addEventListener()`.  
- [document.getElementById()](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)  
- [addEventListener('click', <method to call>)](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)  

Example - code logic:  
```javascript
// 1. Get access to the 'Display Todos' button.
var displayTodosButton = document.getElementById('displayTodosButton');

// 2. Run the displayTodos method, when someone clicks the 'Display Todos' button.
displayTodosButton.addEventListener('click', function() {
  todoList.displayTodos();
});
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
  },
  toggleAll: function() {
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
};

var displayTodosButton = document.getElementById('displayTodosButton');

displayTodosButton.addEventListener('click', function() {
  todoList.displayTodos();
});

```

## Toggle All
In this step, we want to emulate what we did for the 'Display Todos' button, but for `Toggle All`.  

Example - code logic:  
```javascript
// 1. Get access to the 'Toggle All' button.
var toggleAllButton = document.getElementById('toggleAllButton');

// 2. Run the toggleAll method, when someone clicks the 'Toggle All' button.
toggleAllButton.addEventListener('click', function() {
  todoList.toggleAll();
});
``` 

Open `index.html` and make the following changes...  
```html
<!-- Before -->
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <button id="displayTodosButton">Display Todos</button>
    <button>Toggle All</button>
    
    <script src="script.js"></script>
  </body>

</html>

<!-- After -->
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

Now make the following changes to `script.js`...  

Code:  
```javascript
var toggleAllButton = document.getElementById('toggleAllButton');

toggleAllButton.addEventListener('click', function() {
  todoList.toggleAll();
});

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
  },
  toggleAll: function() {
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
};

var displayTodosButton = document.getElementById('displayTodosButton');
var toggleAllButton = document.getElementById('toggleAllButton');

displayTodosButton.addEventListener('click', function() {
  todoList.displayTodos();
});

toggleAllButton.addEventListener('click', function() {
  todoList.toggleAll();
});

```
