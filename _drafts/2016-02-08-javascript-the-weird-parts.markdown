---
layout: post
title:  "JavaScript - the Weird Parts"
date:   2016-02-08 00:00:00 +0800
categories: javascript
---

## First class functions

In JavaScript, we are able to pass functions as arguments like any other variable, because functions are variables.

```js
function foo () {
  // do something here
}
```

This can also be written as:

```js
var foo = function () {
  // do something here
}
```

```js
function add (first, second, callback) {
  var err = null
  var result = null

  if (typeof first === 'number' && typeof second === 'number') {
    result = first + second
  } else {
    err = 'not a number'
  }

  callback(err, result)
}

function callback (err, result) {
  if (err) throw err
  return result
}

add(3, 5, callback)
```

## Event-driven environment

## Closures

## Scope

```js
var a = 3

function foo () {
  var a = 5
  console.log(a) // 5
  console.log(window.a) // 3
}

console.log(a) // 3
console.log(window.a) // 3
```

## Context

## References

[JavaScript is weird... and awesome!][js-video]

[js-video]: https://www.youtube.com/watch?v=JEq7Ehw-qk8&list=PLoYCgNOIyGABI011EYc-avPOsk1YsMUe_&index=1
