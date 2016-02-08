---
layout: post
title:  "JavaScript Design Patterns"
date:   2016-02-08 00:00:00 +0800
categories: javascript
---

## Constructor pattern

```js
function Person (name, age, location) {
  this.name = name
  this.age = age
  this.location = location
  this.introduction = function () {
    return `Hi, my name is ${this.name}. I am ${this.age} and I live in ${location}.`
  }
}
```

To instantiate an object based off the `Person` constructor, we simply use the `new` keyword.

```js
var alfred = new Person('Alfred', 55, Singapore)
var thomas = new Person('Thomas', 35, Malaysia)
```

The problem here is that functions, such as `introduction()`, are redefined for each new object created using the `Person` constructor. Better would be to share functions between instances of the `Person` class.

```js
function Person (name, age, location) {
  this.name = name
  this.age = age
  this.location = location
}

Person.prototype.introduction = function () {
  return `Hi, my name is ${this.name}. I am ${this.age} and I live in ${this.location}.`
}

```

## Module pattern

```js
var Fruit = {
  // properties
  name: 'mango',
  taste: 'sweet',
  // methods
  setName: function (newName) {
    this.name = newName
  }
}
```

```js
var Fruit = (function () {
  // private properties and methods
  var name = 'mango'
  var taste = 'sweet'
  var printToConsole = function (statement) {
    console.log(statement)
  }
  // public properties and methods
  return {
    setName: function (newName) {
      this.name = newName
      printToConsole(`name set to ${newName}`)
    }
  }
})()
```

## References

[Learning JavaScript Design Patterns by Addy Osmani][js-book]
[Modular JavaScript][js-video]

[js-book]: https://addyosmani.com/resources/essentialjsdesignpatterns/book/#constructorpatternjavascript
[js-video]: https://www.youtube.com/watch?v=m-NYyst_tiY&list=PLoYCgNOIyGABs-wDaaxChu82q_xQgUb4f&index=1
