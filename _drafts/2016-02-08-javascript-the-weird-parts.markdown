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

Let's try running this line of code in the console.

```
> console.log(this)
```

When we run `console.log(this)` in the console we get back the `Window` object, so `this` refers to `Window` in this context.

Now let's run this in the console and see what we get back.

```js
function foo () {
  console.log(this)
}

foo() // same as calling window.foo()
```

We still get back `Window` because when we call `foo()` we are actually calling `window.foo()` so `this` will refer to `Window`

## References

[JavaScript is weird... and awesome!][js-video]

[js-video]: https://www.youtube.com/watch?v=JEq7Ehw-qk8&list=PLoYCgNOIyGABI011EYc-avPOsk1YsMUe_&index=1
