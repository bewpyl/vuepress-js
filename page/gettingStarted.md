---
sidebar: auto
---

# Getting Started

## What is JavaScript

JavaScript is a scripting language designed to interact with the elements of web pages. JavaScript consists of three main parts:

- ECMAScript that provides the core functionality.
- The Document Object Model (DOM), which provides interfaces for interacting with elements on web pages
- The Browser Object Model (BOM), which provides interfaces for interacting with the web browsers.

JavaScript allows you to add interactivity to a web page. You usually use JavaScript with HTML and CSS to enhance the functionality of a web page such as creating interactive maps, displaying animated charts.

When a web page is loaded i.e. after HTML and CSS have been downloaded, the web browser’s JavaScript engine starts executing the JavaScript code. The JavaScript code then modifies the HTML and CSS to update the user interface dynamically using DOM interfaces.

### Client-side vs. Server-side JavaScript

When JavaScript is used in a web page, it is executed in the web browsers of user’s computers, therefore, we called JavaScript is client-side language.

JavaScript can run on both the web browsers as well as on the servers. A popular server-side environment for JavaScript is Node.js. Different from the client-side JavaScript, the server-side JavaScript executes on the server and its result is displayed on the web browsers.

### Overview of JavaScript

To [define a variable](http://www.javascripttutorial.net/javascript-variables/) in JavaScript, you use `var` keyword, for example:

```js
var x = 10;
var y = 20;
```

To create a [function](http://www.javascripttutorial.net/javascript-function/), you use the `function` keyword. The following example defines a function that calculates the sum of two arguments:

```js
function add(a,b) {
   return a + b;
}
```


To call the `add()` function, you use the following syntax:

```js
var result = add(x,y);
```

To log the result into the console window, you use `console.log()` e.g.,

```js
console.log(result); 
```

Now you should see `30` in the console window.

JavaScript provides you with the condition statements such as [`if-else`](http://www.javascripttutorial.net/javascript-if-else/) and [`switch`](http://www.javascripttutorial.net/javascript-switch-case/) statements. For example:

```js
var a = 20, 
    b = 30;
 
function divide(a,b) {
    if(b == 0){
        throw new Exception('Division by zero');
    }
    return a / b;
}
```
In the `divide()` function, we checked whether the de-numerator (b) is zero, if it is the case, we threw an exception. Otherwise, we returned the result of a / b.

To declare an [array](http://www.javascripttutorial.net/javascript-array/), you use the following syntax:

```js
var items = [];
```

To declare an array with some initial elements, you use the following form:
```js
var items = [1, 2, 3];
```

You can access the number of elements in the items array through its `length` property.

To iterate over the elements of the `items` array, you use the [`for`](http://www.javascripttutorial.net/javascript-for-loop/) loop statement as follows:

```js
for(var i = 0; i < items.length; i++) {
    console.log(items[i]);
}
```

To declare a “[class](http://www.javascripttutorial.net/javascript-prototype/)” in JavaScript, you use the same `function` keyword e.g.,

```js
function Person(firstName, lastName ){
    this.firstName = firstName;
    this.lastName = lastName;
}
```

The following example declares a method of the `Person` “class”:
```js
Person.prototype.getFullname = function(){
    return this.firstName + ' ' + this.lastName;
}
```

To create an instance of the `Person` “class”, you use the `new` keyword:

```js
var john = new Person('John','Doe');
```

To call the method of the class you can use the (.) operator:

```js
var  fullName = john.getFullname();
```

Since ES6, you can use the [`class`](http://www.javascripttutorial.net/es6/javascript-class/) keyword to declare a class in JavaScript:

```js
class Person {
    constructors(firstName, lastName){
        this.firstName = firstName;
        this.lastName = lastName;
    },
 
    getFullname(){
        return this.firstName + ' ' + this.lastName;
    }
}
```

We have just introduced you some features of JavaScript. You will learn each feature in detail in the subsequent tutorials.

Having fun learning JavaScript!


## JavaScript Hello World Example

**Summary**: This tutorial gets you started with JavaScript by showing you how to embed JavaScript code into an HTML page and helps you develop JavaScript Hello World page.


1. Embed JavaScript code directly into the HTML page.
2. Reference to an external JavaScript code file.

### Embed JavaScript code in an HTML page



