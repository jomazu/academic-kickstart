---
title: Loops
linktitle: JS Loops, ch-05
toc: true
type: docs
date: "2017-12-04T00:00:00+01:00"
lastmod: "2017-12-04T00:00:00Z"
draft: false
menu:
  js_fundamentals:
    parent: JavaScript
    weight: 7

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 7
---

## FOR LOOP
The `for loop` allows you to repeat a certain amount of code any number of times.  

Example in plain english, not code:  
```javascript
// Keep track of a variable (i) and set it to (0)
i = 0               // Initialization
Say "hey" if i < 3  // Condition
Increase i by 1     // Final-expression

// This is what the computer is actually doing
0 "hey" // i=0, say 'hey'
1 "hey" // i=1, say 'hey'
2 "hey" // i=2, say 'hey'
3       // i=3, code stops (3 is not less than 3)

for (initialization; condition; final-expression) {
  console.log('hey');
}
```

```javascript
> for (var i = 0; i < 3; i++) {
    console.log(`Number: ${i}`);
  }

Number: 0
Number: 1
Number: 2

> for (var i = 0; i < 10; i = i + 2) {
    console.log(`Number: ${i}`);
  }

Number: 0
Number: 2
Number: 4
Number: 6
Number: 8
```

## LOOPING over Arrays
Example using an array:  
```javascript
> var testArray = ['item 1', 'item 2', 'item 3'];

> for (var i = 0; i < testArray.length; i++) {
    console.log(`Array index (${i}): ${testArray[i]}`);
  }

Array index (0): item 1
Array index (1): item 2
Array index (2): item 3

// Turn the above FOR LOOP into a function, so it can be called repeatedly
> function forLoop() {
    for (var i = 0; i < testArray.length; i++) {
      console.log(`Array index (${i}): ${testArray[i]}`);
    })
  };

// Add a new item to the original array
> testArray.push('testArray.push');

> forLoop();

Array index (0): item 1
Array index (1): item 2
Array index (2): item 3
Array index (3): testArray.push
```

Note: create the `for loop` first, then create a `function` to house (run) it.  