---
title: Thinking in Code
linktitle: Thinking in Code, ch-06
toc: true
type: docs
date: "2017-12-06T00:00:00+01:00"
lastmod: "2017-12-06T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 9

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 9
---

## Requirements
The requirements for this chapter:  

- `.toggleAll` : If everything is **TRUE**, make everything **FALSE**  
- `.toggleAll` : Otherwise, make everything **TRUE**  

In this section, we are going to work on one feature that toggle's all the todos as complete or incomplete.  

## .toggleAll  
Case 1  

If all todos are marked as complete (i.e. TRUE), then toggling them will make everything FALSE.  

Example - logic:  
```javascript
toggleAll: function() {
  // Create variable to count total todos.
  var totalTodos = this.todos.length;
  // Create variable to count completed todos.
  var completedTodos = 0;
  // Get number of completed todos.
  for (var i = 0; i < totalTodos; i++) {
    if (this.todos[i].completed === true) {
      completedTodos++;
    }
  }
  // Case 1:
  // If everything's true, make everything false.
  if (completedTodos === totalTodos) {
    // Make everything false.
    for (var i = 0; i < totalTodos; i++) {
      this.todos[i].completed = false;
    }
  }
}
```

Example - code:  
```javascript
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
  }
  this.displayTodos();
}
```

Add the new `toggleAll` method to our `todoList` object in Plunker:  

Before...  
```javascript
toggleCompleted: function(position) {
    var todo = this.todos[position];
    todo.completed = !todo.completed;
    this.displayTodos();
  }
  // Add new toggleAll method here
};
```

After...  
```javascript
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
    }
    this.displayTodos();
  }
};

```

Test in Plunker:  
```javascript
> todoList.addTodo('item 1');
My Todos:
( ) item 1

> todoList.addTodo('item 2');
My Todos:
( ) item 1
( ) item 2

> todoList.toggleCompleted(0);
My Todos:
(x) item 1
( ) item 2

> todoList.toggleCompleted(1);
My Todos:
(x) item 1
(x) item 2

> todoList.toggleAll();
My Todos:
( ) item 1
( ) item 2
```

## .toggleAll  
Case 2  

If some todos are marked as complete (i.e. TRUE) and some are marked as FALSE, make everything TRUE.  

Before...  
```javascript
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
    } // Add Case 2 (else) clause here
    this.displayTodos();
  }
};

```

After...  
```javascript
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

Test in Plunker:  
```javascript
> todoList.addTodo('item 1');
My Todos:
( ) item 1

> todoList.addTodo('item 2');
My Todos:
( ) item 1
( ) item 2

> todoList.addTodo('item 3');
My Todos:
( ) item 1
( ) item 2
( ) item 3

> todoList.toggleAll();
(x) item 1
(x) item 2
(x) item 3

> todoList.toggleAll();
( ) item 1
( ) item 2
( ) item 3

> todoList.toggleCompleted(0);
My Todos:
(x) item 1
( ) item 2
( ) item 3

> todoList.toggleCompleted(2);
My Todos:
(x) item 1
( ) item 2
(x) item 3

> todoList.toggleAll();
My Todos:
(x) item 1
(x) item 2
(x) item 3
```
