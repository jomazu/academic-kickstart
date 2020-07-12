---
title: Data from Inputs
linktitle: Inputs, ch-08b
toc: true
type: docs
date: "2017-12-10T00:00:00+01:00"
lastmod: "2017-12-10T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 14

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 14
---

## Requirements
The requirements for this chapter:  

- It should have **working controls** for `.addTodo`  
- It should have **working controls** for `.changeTodo`  
- It should have **working controls** for `.deleteTodo`  
- It should have **working controls** for `.toggleCompleted`  

The requirements in this section are different from previous sections, because they require inputs - i.e. enable someone to type something into a text box and then click it. Each of the methods indicated above requires an argument. 

## addTodo
Provide text for the new todo object.  

Previous `index.html`...  
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

New `index.html`...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <div>
      <button onclick="handlers.displayTodos()">Display Todos</button>
      <button onclick="handlers.toggleAll()">Toggle All</button>
    </div>
    
    <div>
      <button onclick="handlers.addTodo()">Add</button>
      <input id="addTodoTextInput" type="text">
    </div>
    
    <script src="script.js"></script>
  </body>

</html>
```

Previous `script.js`...  
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

New `script.js`...  
```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  toggleAll: function() {
    todoList.toggleAll();
  },
  addTodo: function() {
    var addTodoTextInput = document.getElementById('addTodoTextInput');
    todoList.addTodo(addTodoTextInput.value);
    // This line will clear the Text Input box
    addTodoTextInput.value = '';
  }
};
```

## changeTodo
Tell the changeTodo method which todo to change, and then give it some new text.  

Previous `index.html`...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <div>
      <button onclick="handlers.displayTodos()">Display Todos</button>
      <button onclick="handlers.toggleAll()">Toggle All</button>
    </div>
    
    <div>
      <button onclick="handlers.addTodo()">Add</button>
      <input id="addTodoTextInput" type="text">
    </div>
    
    <script src="script.js"></script>
  </body>

</html>
```

New `index.html`...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <div>
      <button onclick="handlers.displayTodos()">Display Todos</button>
      <button onclick="handlers.toggleAll()">Toggle All</button>
    </div>
    
    <div>
      <button onclick="handlers.addTodo()">Add</button>
      <input id="addTodoTextInput" type="text">
    </div>
    
    <div>
      <button onclick="handlers.changeTodo()">Change Todo</button>
      <input id="changeTodoPositionInput" type="number">
      <input id="changeTodoTextInput" type="text">
    </div>
    
    <script src="script.js"></script>
  </body>

</html>
```

Previous `script.js`...  
```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  toggleAll: function() {
    todoList.toggleAll();
  },
  addTodo: function() {
    var addTodoTextInput = document.getElementById('addTodoTextInput');
    todoList.addTodo(addTodoTextInput.value);
    addTodoTextInput.value = '';
  }
};
```

New `script.js`...  
```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  toggleAll: function() {
    todoList.toggleAll();
  },
  addTodo: function() {
    var addTodoTextInput = document.getElementById('addTodoTextInput');
    todoList.addTodo(addTodoTextInput.value);
    addTodoTextInput.value = '';
  },
  changeTodo: function() {
    var changeTodoPositionInput = document.getElementById('changeTodoPositionInput');
    var changeTodoTextInput = document.getElementById('changeTodoTextInput');
    // First argument is a number, so use: .valueAsNumber
    // Second argument is text, so use: .value
    todoList.changeTodo(changeTodoPositionInput.valueAsNumber, changeTodoTextInput.value);
    // Clear the number position box
    changeTodoPositionInput.value = '';
    // Clear the text input box
    changeTodoTextInput.value = '';
  }
};
```

## deleteTodo
Tell the deleteTodo method which todo to delete.  

Previous `index.html`...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <div>
      <button onclick="handlers.displayTodos()">Display Todos</button>
      <button onclick="handlers.toggleAll()">Toggle All</button>
    </div>
    
    <div>
      <button onclick="handlers.addTodo()">Add</button>
      <input id="addTodoTextInput" type="text">
    </div>
    
    <div>
      <button onclick="handlers.changeTodo()">Change Todo</button>
      <input id="changeTodoPositionInput" type="number">
      <input id="changeTodoTextInput" type="text">
    </div>
    
    <script src="script.js"></script>
  </body>

</html>
```

New `index.html`...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <div>
      <button onclick="handlers.displayTodos()">Display Todos</button>
      <button onclick="handlers.toggleAll()">Toggle All</button>
    </div>
    
    <div>
      <button onclick="handlers.addTodo()">Add</button>
      <input id="addTodoTextInput" type="text">
    </div>
    
    <div>
      <button onclick="handlers.changeTodo()">Change Todo</button>
      <input id="changeTodoPositionInput" type="number">
      <input id="changeTodoTextInput" type="text">
    </div>
    
    <div>
      <button onclick="handlers.deleteTodo()">Delete</button>
      <input id="deleteTodoPositionInput" type="number">
    </div>
    
    <script src="script.js"></script>
  </body>

</html>
```

Previous `script.js`...  
```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  toggleAll: function() {
    todoList.toggleAll();
  },
  addTodo: function() {
    var addTodoTextInput = document.getElementById('addTodoTextInput');
    todoList.addTodo(addTodoTextInput.value);
    addTodoTextInput.value = '';
  },
  changeTodo: function() {
    var changeTodoPositionInput = document.getElementById('changeTodoPositionInput');
    var changeTodoTextInput = document.getElementById('changeTodoTextInput');
    todoList.changeTodo(changeTodoPositionInput.valueAsNumber, changeTodoTextInput.value);
    changeTodoPositionInput.value = '';
    changeTodoTextInput.value = '';
  }
};
```

New `script.js`...  
```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  toggleAll: function() {
    todoList.toggleAll();
  },
  addTodo: function() {
    var addTodoTextInput = document.getElementById('addTodoTextInput');
    todoList.addTodo(addTodoTextInput.value);
    addTodoTextInput.value = '';
  },
  changeTodo: function() {
    var changeTodoPositionInput = document.getElementById('changeTodoPositionInput');
    var changeTodoTextInput = document.getElementById('changeTodoTextInput');
    todoList.changeTodo(changeTodoPositionInput.valueAsNumber, changeTodoTextInput.value);
    changeTodoPositionInput.value = '';
    changeTodoTextInput.value = '';
  },
  deleteTodo: function() {
    var deleteTodoPositionInput = document.getElementById('deleteTodoPositionInput');
    todoList.deleteTodo(deleteTodoPositionInput.valueAsNumber);
    deleteTodoPositionInput.value = '';
  }
};
```

## toggleCompleted
Tell the toggleCompleted method which todo to change to completed.  

Previous `index.html`...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <div>
      <button onclick="handlers.displayTodos()">Display Todos</button>
      <button onclick="handlers.toggleAll()">Toggle All</button>
    </div>
    
    <div>
      <button onclick="handlers.addTodo()">Add</button>
      <input id="addTodoTextInput" type="text">
    </div>
    
    <div>
      <button onclick="handlers.changeTodo()">Change Todo</button>
      <input id="changeTodoPositionInput" type="number">
      <input id="changeTodoTextInput" type="text">
    </div>
    
    <div>
      <button onclick="handlers.deleteTodo()">Delete</button>
      <input id="deleteTodoPositionInput" type="number">
    </div>
    
    <script src="script.js"></script>
  </body>

</html>
```

New `index.html`...  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Todo List</h1>
    
    <div>
      <button onclick="handlers.displayTodos()">Display Todos</button>
      <button onclick="handlers.toggleAll()">Toggle All</button>
    </div>
    
    <div>
      <button onclick="handlers.addTodo()">Add</button>
      <input id="addTodoTextInput" type="text">
    </div>
    
    <div>
      <button onclick="handlers.changeTodo()">Change Todo</button>
      <input id="changeTodoPositionInput" type="number">
      <input id="changeTodoTextInput" type="text">
    </div>
    
    <div>
      <button onclick="handlers.deleteTodo()">Delete</button>
      <input id="deleteTodoPositionInput" type="number">
    </div>
    
    <div>
      <button onclick="handlers.toggleCompleted()">Toggle Completed</button>
      <input id="toggleCompletedPositionInput" type="number">
    </div>
    
    <script src="script.js"></script>
  </body>

</html>
```

Previous `script.js`...  
```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  toggleAll: function() {
    todoList.toggleAll();
  },
  addTodo: function() {
    var addTodoTextInput = document.getElementById('addTodoTextInput');
    todoList.addTodo(addTodoTextInput.value);
    addTodoTextInput.value = '';
  },
  changeTodo: function() {
    var changeTodoPositionInput = document.getElementById('changeTodoPositionInput');
    var changeTodoTextInput = document.getElementById('changeTodoTextInput');
    todoList.changeTodo(changeTodoPositionInput.valueAsNumber, changeTodoTextInput.value);
    changeTodoPositionInput.value = '';
    changeTodoTextInput.value = '';
  },
  deleteTodo: function() {
    var deleteTodoPositionInput = document.getElementById('deleteTodoPositionInput');
    todoList.deleteTodo(deleteTodoPositionInput.valueAsNumber);
    deleteTodoPositionInput.value = '';
  }
};
```

New `script.js`...  
```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  toggleAll: function() {
    todoList.toggleAll();
  },
  addTodo: function() {
    var addTodoTextInput = document.getElementById('addTodoTextInput');
    todoList.addTodo(addTodoTextInput.value);
    addTodoTextInput.value = '';
  },
  changeTodo: function() {
    var changeTodoPositionInput = document.getElementById('changeTodoPositionInput');
    var changeTodoTextInput = document.getElementById('changeTodoTextInput');
    todoList.changeTodo(changeTodoPositionInput.valueAsNumber, changeTodoTextInput.value);
    changeTodoPositionInput.value = '';
    changeTodoTextInput.value = '';
  },
  deleteTodo: function() {
    var deleteTodoPositionInput = document.getElementById('deleteTodoPositionInput');
    todoList.deleteTodo(deleteTodoPositionInput.valueAsNumber);
    deleteTodoPositionInput.value = '';
  },
  toggleCompleted: function() {
    var toggleCompletedPositionInput = document.getElementById('toggleCompletedPositionInput');
    todoList.toggleCompleted(toggleCompletedPositionInput.valueAsNumber);
    toggleCompletedPositionInput.value = '';
  }
};
```

## Re-order Handlers Methods
Re-ordered the Handlers methods to coincide with the todoList object order sequence.  

```javascript
var handlers = {
  displayTodos: function() {
    todoList.displayTodos();
  },
  addTodo: function() {
    var addTodoTextInput = document.getElementById('addTodoTextInput');
    todoList.addTodo(addTodoTextInput.value);
    addTodoTextInput.value = '';
  },
  changeTodo: function() {
    var changeTodoPositionInput = document.getElementById('changeTodoPositionInput');
    var changeTodoTextInput = document.getElementById('changeTodoTextInput');
    todoList.changeTodo(changeTodoPositionInput.valueAsNumber, changeTodoTextInput.value);
    changeTodoPositionInput.value = '';
    changeTodoTextInput.value = '';
  },
  deleteTodo: function() {
    var deleteTodoPositionInput = document.getElementById('deleteTodoPositionInput');
    todoList.deleteTodo(deleteTodoPositionInput.valueAsNumber);
    deleteTodoPositionInput.value = '';
  },
  toggleCompleted: function() {
    var toggleCompletedPositionInput = document.getElementById('toggleCompletedPositionInput');
    todoList.toggleCompleted(toggleCompletedPositionInput.valueAsNumber);
    toggleCompletedPositionInput.value = '';
  },
  toggleAll: function() {
    todoList.toggleAll();
  }
};

```
