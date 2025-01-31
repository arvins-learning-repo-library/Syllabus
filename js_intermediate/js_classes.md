# JavaScript Classes
Classes are a particular type of function that contain data and behavior. Classes are the blueprints of objects. Just like functions, classes have their own scope.

There are particular JavaScript keywords that are used to create and access information within a class:
- `constructor`: a special method for creating and initializing objects
- `this`: a JavaScript keyword that refers to the object it belongs to
- `new`: used when creating a new instance of a class (an object)

Class syntax conventions:

- Class names are always capitalized
- Class names are PascalCased (like camelCase, but the first word is capitalized)
- Instance of classes (objects) are always lowercase

```JavaScript
class Squirrel{
  constructor(){
    this.nutCount = 0
  }

  storeNut(){
    this.nutCount += 1
  }

  eatNut(){
    this.nutCount -= 1
  }
}
// creating the instance of the class, saved as a variable
// rocky now has access to the class methods
var rocky = new Squirrel()

console.log(rocky.nutCount)
// Output -->> 0
rocky.storeNut()
console.log(rocky.nutCount)
// Output -->> 1
rocky.storeNut()
console.log(rocky.nutCount)
// Output -->> 2
rocky.eatNut()
console.log(rocky.nutCount)
// Output -->> 1
```

Just like functions, classes are reusable. Each object created from the class is independent from each other.

```JavaScript
class Squirrel{
  constructor(){
    this.nutCount = 0
  }

  storeNut(){
    this.nutCount += 1
  }

  eatNut(){
    this.nutCount -= 1
  }
}

var rocky = new Squirrel()
var alvin = new Squirrel()

alvin.storeNut()
alvin.storeNut()

console.log("Rocky has ", rocky.nutCount )
// Output -->> Rocky has 0
console.log("Alvin has ", alvin.nutCount )
// Output -->> Alvin has 2
```

Class instances can be used like any other 'thing' in JavaScript. We can rewrite the above like this:

```JavaScript
class Squirrel{
  constructor(){
    this.nutCount = 0
  }

  storeNut(){
    this.nutCount += 1
  }

  eatNut(){
    this.nutCount -= 1
  }
}
// create a new array
var squirrels = []
// pushes new squirrel objects into the array
squirrels.push(new Squirrel())
squirrels.push(new Squirrel())

// accessing the object at array index 0
squirrels[0].storeNut()
squirrels[0].storeNut()

// mapping over array to access the information from the squirrels array
squirrels.map((value, index) => {
  console.log(`The squirrel at index ${index} has ${value.nutCount} nuts.`)
})
```

Class instances can store any kind of data.

```javascript
class DiceRoller{
  constructor(){
    this.rolls = []
  }

  roll(){
    // generating a random number between 1 and 6 and pushing to the this.rolls array
    this.rolls.push(Math.ceil(Math.random() * 6))
  }

  lastRoll(){
    //logging the last roll added to the array
    return this.rolls[this.rolls.length - 1]
  }
}

var roller = new DiceRoller()
console.log("Roll:", roller.lastRoll())
// Output -->> Roll: undefined
roller.roll()
console.log("Roll:", roller.lastRoll())
// Output -->> Roll: 6
roller.roll()
console.log("Roll:", roller.lastRoll())
// Output -->> Roll: 4
console.log("All Rolls:", roller.rolls)
// Output -->> All Rolls: [ 6, 4 ]
```
The constructor method can take arguments. This creates objects with unique data.

```JavaScript
class Dog{
  constructor(name, age){
    this.name = name
    this.age = age
  }

  description(){
    return `${this.name} is a ${this.age} year old dog.`
  }
}
// now when creating the new object, the constructor method is expecting two arguments: a name and an age
var rover = new Dog('Rover', 4)
console.log(rover.description())
// Output -->> Rover is a 4 year old dog.
```
We can use the Dog class to create many different dog objects with different properties.

```JavaScript
var plato = new Dog('Plato', 8)
var bella = new Dog('Bella', 11)
console.log(plato.description())
// Output -->> Plato is a 8 year old dog.
console.log(bella.description())
// Output -->> Bella is a 11 year old dog.
```

Objects are still just variables that reference a class. Variables in JavaScript can be reassigned.

```JavaScript
var plato = new Dog('Plato', 8)
var bella = new Dog('Bella', 11)

console.log(plato.description())
// Output -->> Plato is a 8 year old dog.
console.log(bella.description())
// Output -->> Bella is a 11 year old dog.
bella = plato
console.log(bella.description())
// Output -->> Plato is a 8 year old dog.
// !!!! bella got reassigned
```

## Resources

For more information on objects see:
<a href="http://www.javascriptenlightenment.com/" target="_blank">Javascript Enlightenment</a>
<a href="https://github.com/getify/You-Dont-Know-JS/blob/master/up%20&%20going/ch2.md#objects" target="_blank">You Don't Know JS: Up & Going - Chapter 2: Into JavaScript</a>
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript#Objects" target="_blank">MDN: Objects</a>

For more information on closures see:
<a href="http://www.javascriptenlightenment.com/" target="_blank">Javascript Enlightenment</a>, chapter 7.
<a href="https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch3.md#chapter-3-function-vs-block-scope" target="_blank">You Don't Know JS: Function vs. Block Scope</a>
<a href="https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch5.md#chapter-5-scope-closure" target="_blank">You Don't Know JS: Scope Closure</a>
(Caution: not for the faint of heart)

A great style guide for Javascript:
[Air B & B](https://github.com/airbnb/javascript)


You can see this animated if you go to http://pythontutor.com, select javaScript, and paste in the code.
For further in-depth information see <a href="http://www.javascriptenlightenment.com/" target="_blank">Javascript Enlightenment</a>

## Challenges

1. Coffee Maker

```javascript
class Coffee {
  constructor(type, cream, sugar){
    this.type = type.toLowerCase()
    this.cream = cream
    this.sugar = sugar
  }

  coffeeProfile(){
    return(`${this.type}: ${this.creams()}, ${this.sugars()}`)
  }

  creams(){
    if (this.cream > 1){
      return `${this.cream} creams`
    } else {
      return `${this.cream} cream`
    }
  }

  sugars(){
    if (this.sugar > 1){
      return `${this.sugar} sugars`
    } else {
      return `${this.sugar} sugar`
    }
  }
}
```

- Write the code that makes a black coffee.

- Write the code that makes a coffee with 1 cream and 2 sugars.

- Write the code that makes a coffee with 2 sugars. Then write the code that outputs the coffee's profile.

2. Latte Maker

- Write a Latte class that receives a flavor, a milk type and a number of shots.

- Write a method for your Latte class that outputs the latte's profile.

- Write the code that makes a regular, single shot latte. Then, log the latte's profile.

- Write the code that makes a double shot hazelnut latte with almond milk. Then, log the latte's profile.

3. Volume of a Cylinder

- Write a class that calculates the volume of a Cylinder to four decimal places. Volume of a cylinder : V = πr2h (r is the radius and h is the height of the cylinder)

- Write the code that creates three unique cylinder objects

[Go to next lesson: JavaScript Inheritence](../js_intermediate/05js_class_inheritance.md)

[Back to JavaScript Classes](../js_intermediate/js_classes.md)

[Back to Syllabus](../README.md)
