---
title: Data Types and Comparisons
linktitle: Data Types, ch-06b
toc: true
type: docs
date: "2017-12-09T00:00:00+01:00"
lastmod: "2017-12-09T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 10

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 10
---

## JavaScript Data Types
- **OBJECTS** `{ }` - can be as complex as you want  

Example:  
```javascript
var todoList = { 
  todos: [], 
  addTodo: function(todoText) {
    this.todos.push({
      todoText: todoText,
      completed: false
    });
  } 
};
```  

- **PRIMITIVES** - building blocks  
  - String - `This is a string!`  
  - Number - `1, 2, 3, 4 ...`  
  - Boolean - `true` or `false`  
  - Undefined - a value that hasn't been set  
  - Null - `Nothing`  

## Comparisons with PRIMITIVES (Values)
Strings  
```javascript
> 'john' === 'john';
true

> 'john1' === 'john';
false
```

Numbers  
```javascript
> 1 === 1;
true

> 1 === 2;
false

> 36 === '36';
false
```

Booleans  
```javascript
> true === true;
true

> true === false;
false

> false === false;
true
```

Undefined and Null  
```javascript
> undefined === undefined;
true

> null === null;
true
```

## Comparisons of OBJECTS (References)
The following examples are FALSE, because the **REFERENCES** (addresses in memory) differ for each object.  

```javascript
> {} === {}
false

> [1, 2, 3] === [1, 2, 3]
false
```
The examples below are TRUE, because the **REFERENCES** (addresses in memory) for the VARIABLES are the same.  

```javascript
> var arrayOne = [1, 2, 3];

> arrayOne;
[1, 2, 3]

// arrayOne (reference) === arrayOne (reference)
> arrayOne === arrayOne;
true

> var objectOne = {};

// objectOne (reference) === objectOne (reference)
> objectOne === objectOne;
true
```

Additional code examples...  
```javascript
/* ------ Example 1 ------ */
> var myPrimitive = 10;
> myPrimitive;
10

> var myObject = { name: 'John' };
> myObject.name;
'John'

/* ------ Example 2 ------ */
> var myHouse = { color: 'blue' };
> myHouse.color;
'blue'

// Access the property on an object and change it
> myHouse.color = 'red';
> myHouse.color;
'red'

/* ------ Example 3 ------ */
> var myHouse = { color: 'blue' };
> myHouse.color;
'blue'

> var color = myHouse.color;
> color;
'blue'

> color = 'red';
> color
'red'

/* ------ Example 4 ------ */
> var myHouse1 = { color: 'blue' };
> var myHouse2 = myHouse1;

> myHouse1.color;
'blue'

> myHouse2.color;
'blue'

> myHouse2.color = 'red';

> myHouse1.color;
'red'

> myHouse2.color;
'red'

/* ------ Example 5 ------ */
> var myHouse1 = { color: 'blue' };
> var myHouse2 = { color: 'blue' };

> myHouse2.color = 'red';

> myHouse1.color;
'blue'

> myHouse2.color;
'red'
```
