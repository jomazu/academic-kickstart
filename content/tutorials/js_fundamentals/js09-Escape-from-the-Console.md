---
title: Escape from The Console
linktitle: Escape the Console, ch-09
toc: true
type: docs
date: "2017-12-10T00:00:00+01:00"
lastmod: "2017-12-10T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 15

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 15
---

## Requirements
The requirements for this chapter:  

- There should be an `li` element for **every todo**  
- Each `li` element should **contain** `.todoText`  
- Each `li` element should **show** `.completed`   

## Escape From The Console
In our app, we do not know how many items will be in the **unordered list**. Additionally, the items can change over time - i.e. delete an item or add an item etc. Thus, we need to dynamically add items to the list and delete items from the list.  

But, first we need to know how to insert list items into the DOM. To do this, we will use JavaScript to dynamically insert list elements into the unordered list.  

Console examples below...  

Use a JS variable to dynamically create a LIST item:  
- [document.createElement()](https://www.w3schools.com/jsref/met_document_createelement.asp)  
```javascript
> var todoLi = document.createElement('li');

> todoLi;
    <li></li>
```  

Create a variable to grab or reference an element, in this case, the UNORDERED list element:  
- [document.querySelector()](https://www.w3schools.com/jsref/met_document_queryselector.asp)  
```javascript
> var todosUl = document.querySelector('ul');

> todosUl;
    <ul>
        </ul>
```

To append a node as the last child of a node, we use the following:  
- [appendChild()](https://www.w3schools.com/jsref/met_node_appendchild.asp)  
```javascript
> todosUl.appendChild(todoLi);
    <li></li>
```

## TO BE CONTINUED...