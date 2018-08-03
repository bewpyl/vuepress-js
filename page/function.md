---
sidebar: auto
---

# JavaScript function

## JavaScript function

**Summary**: this tutorial introduces you to JavaScript function concept that allows you to structure your code into smaller and reusable units.

One of the most important concepts in JavaScript is the function. The functions allow you to structure a large script, reduce into smaller manageable units.

### Declaring JavaScript function

To declare a function, you use the `function` keyword, followed by the function name, a list of arguments, and then the function body.

The basic syntax for declaring a function is as follows:

| 123  | function functionName(argument0,argument1,argumentN){    // function body} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

The function name must be a valid JavaScript [identifier](http://www.javascripttutorial.net/javascript-syntax/#identifiers).

See the following example.

| 1234567 | function say(message) {    if (message) {        alert('Hello');    } else {        alert(message);    }} |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

The function `say` accepts one argument. Inside the function, it shows the `Hello` message if the `message` argument is blank, otherwise, it shows the value of the  `message` argument.

### Calling a JavaScript function

To call a function, you use its name followed by the function arguments enclosed in parentheses. If the function accepts multiple arguments, you separate arguments by commas.

The following statement calls the `say()` function above.

| 1    | say('Hi'); |
| ---- | ---------- |
|      |            |

The output of the function is `'Hi'`.

### Returning a value

A function can return a value by using the `return` statement followed by an expression or a value. See the following example.

| 123  | function add(a, b) {    return a + b;} |
| ---- | -------------------------------------- |
|      |                                        |

The `add` function adds two values and returns the result.

You can call the `add()` function as follows:

| 1    | var result = add(10,20); |
| ---- | ------------------------ |
|      |                          |

You can use multiple `return` statements in a function to return different values based on a condition as shown in the following example.

| 1234567891011 | function compare(a, b) {    if (a > b) {        return -1;    }    else if (a < b) {        return 1;    }    else {        return 0;    }} |
| ------------- | ------------------------------------------------------------ |
|               |                                                              |

The `compare()` function compares two values. It returns -1 if the first argument is greater than the second one, 1 if the first argument is less than the second one, and 0 in case they are equal.

It’s important to note that a function stops executing and exits immediately when the `return` statement is reached. For this reason, you can use the `return` statement to stop the execution of a function immediately.

See the following function.

| 12345678 | function logUsername(username) {    console.log('username:' + username);    // log a message if the name is too short    if (username.length > 5) {        return;    }    console.log('User name ' + username + ' is too short!!!');} |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

The `logUsername()` function accepts an argument which is the `username`. On line 4, if the length of the `username` argument is greater than 5, the function stops and line 7 will not be executed at all.

### Understanding JavaScript function arguments

Different from other programming languages, JavaScript treats function arguments differently.

You can define a function that accepts three arguments. However, it does not mean that you can pass in only three arguments in. Actually, you can pass in three, one or none, and the JavaScript interpreter won’t complain at all.

In fact, JavaScript uses an object named `arguments` to represent a function argument. The `arguments`object behaves like an array though it is not an instance of Array.

For example, you can use the square bracket `[]` to access the arguments: `arguments[0]` returns the first argument, `arguments[1]` returns the second one, and so on. Also, you can use the `length`property of the `arguments` object to determine the number of the input arguments.

The following example shows a generic `add()` function that calculates the sum of any numbers of arguments.

| 1234567 | function add() {    var sum = 0;    for (let i = 0; i < arguments.length; i++) {        sum += arguments[i];    }    return sum;} |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

Hence, you can pass any number of arguments to the `add()` function.

| 12   | console.log(add(1, 2)); // 3console.log(add(1, 2, 3, 4, 5)); // 15 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

### JavaScript function overloading

In other programming languages, it is possible to have two or more functions that share the same name as long as their signatures are different. However, you cannot do it in JavaScript.

See the following example.

| 123456789 | function addTen(a) {    return a + 10;} function addTen(a, b) {    return a + b + 10;}var result = addTen(100);console.log(result); // ? |
| --------- | ------------------------------------------------------------ |
|           |                                                              |

The first `addTen()` function accepts an argument. It adds 10 to that argument.

The second `addTen()` function accepts two arguments. It adds 10 to the sum of the two arguments.

On the next line, we call the `addTen()` function and pass one argument, and then set the return value of the function to the `result` variable.

What is the value of the `result` variable?

It’s `NaN`.

Here is how it works.

The second version of the `addTen()` function overwrites the first one. When we pass one argument to the `addTen()` function that accepts two arguments, the value of the second argument is [`undefined`](http://www.javascripttutorial.net/javascript-data-types/#undefined).  This is like when we declare a [variable](http://www.javascripttutorial.net/javascript-variables/) without initializing it. The function performs the following calculation:

| 1    | 100 + undefined + 10; |
| ---- | --------------------- |
|      |                       |

It returns `undefined`.

Internally, a function name is like a pointer that points to a `Function` object, therefore, you can rewrite the `addTen` functions as follows:

| 123456789 | var addTen = function(a){   return a + 10;} var addTen = function(a,b){    return a + b + 10;}var result = addTen(10);console.log(result); // undefined |
| --------- | ------------------------------------------------------------ |
|           |                                                              |

You will learn more about this syntax in the [Function type tutorial](http://www.javascripttutorial.net/javascript-function-type/).

### JavaScript function hoisting

In JavaScript, it is possible to use a function before it is declared. See the following example.

| 12345 | showMe(); // an hoisting example function showMe(){    console.log('an hoisting example');} |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

This feature is called [hoisting](http://www.javascripttutorial.net/javascript-variables/#hoisting). Internally, there are two phases happening in the JavaScript engine when it executes the code: compilation and execution.

1. In the compilation phase, JavaScript engine moves all the function declarations (and also variable declarations) to the top of its current context. We say that function declarations are hoisted.
2. In the execution phase, JavaScript engine just executes the code.

So this is what happening internally in the JavaScript engine of the script above:

| 12345 | function showMe(){    console.log('an hoisting example');} showMe(); // an hoisting example |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

JavaScript engines move the `showMe()` function declaration to the top therefore the code works fine.

Now you should have a good understanding of the JavaScript function and know how to organize your code using functions.


## JavaScript Function Type

**Summary**: in this tutorial, you will learn about the JavaScript Function type that allows you to use functions as objects.

### Introduction to JavaScript Function type

Unlike other programming languages, [JavaScript functions](http://www.javascripttutorial.net/javascript-function/) are objects. In other words, a function is an instance of the `Function` type. Because a function is an object, it has properties and methods like other objects. Also, the name of a function is just a pointer that points to the function object.

See the following `add()` function.

| 123  | function add(a, b) {    return a + b;} |
| ---- | -------------------------------------- |
|      |                                        |

It is equivalent to the following syntax.

| 123  | var add = function () {    return a + b;}; |
| ---- | ------------------------------------------ |
|      |                                            |

This syntax is called *function expression*. In this syntax, we declare a variable named `add` and initialize it to a function.

Note that there is no name that follows the `function` keyword because it is not necessary. The reason is that you can reference to the function through the  `add` variable. Also, there is a semicolon (;) at the end of the function to indicate the end of the variable declaration statement.

Now, you can call the function using the following syntax:

| 12   | var result = add(10, 20);console.log(result); // 30 |
| ---- | --------------------------------------------------- |
|      |                                                     |

Because `add` is a variable, you can assign it to another variable as follows.

| 12   | var sum = add;console.log(sum(100,200)); |
| ---- | ---------------------------------------- |
|      |                                          |

Now both the `add` and `sum` variables (pointers) are pointing to the same function.

Even though the `add` function is set to [`null`](http://www.javascripttutorial.net/javascript-data-types/#null), you still can access the function using the `sum` variable as follows:

| 12   | add = null;console.log(sum(1,2)); // 3 |
| ---- | -------------------------------------- |
|      |                                        |

### Function expression and hoisting

All [function declarations are hoisted](http://www.javascripttutorial.net/javascript-function/#hoisting) but function expressions are not.

The following script works perfectly fine because the `greeting()` function is hoisted. In other words, its declaration is moved to the top in the compilation phase.

| 1234 | greeting(); // Hifunction greeting() { // greeting is hoisted    alert('Hi');} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

However, this will not work.

| 1234 | sayHi(); // TypeErrorvar sayHi = function () {    alert('Hi');}; |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

You get an error message `TypeError: sayHi is not a function`.

### Functions properties

Each function object has two properties: `length` and `prototype`.

- The `length` property determines the number of named arguments specified in the function declaration.
- The `prototype` property points to the function object.

See the following example:

| 12345678 | function swap(x, y) {    let tmp = x;    x = y;    y = tmp;} console.log(swap.length); // 2console.log(swap.prototype); // Object{} |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

The `swap()` function accepts two arguments `x` and `y`, therefore, the `length` property returns 2. We will discuss `prototype` property in more detail in the prototype tutorial.

### Function methods: apply(), call() and bind()

A function object has three methods: `apply()`, `call()` and `bind()`.

#### The apply() and call() methods, apply() vs. call()

The `apply()` and `call()` functions call a function with a given this value and provided arguments. The difference between the `apply()` and `call()` function is that you need to pass the arguments to the `apply()` function as an array-like object, whereas you have to pass the arguments to the `call()`function individually.

See the following code.

| 12345678 | var cat = {type: 'Cat', sound: 'Meow'};var dog = {type: 'Dog', sound: 'Woof'}; var say = function (greeting) {    console.log(greeting);    // access current this    console.log(this.type + ' says ' + this.sound);}; |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

First, we declare two objects `cat` and `dog` with two properties. Then, we declare the `say()` function that accepts one argument.

You can call the `say()` function through the `apply()` method as follows:

| 123  | say.apply(cat, ['Hi']);// Hi// Cat says Meow |
| ---- | -------------------------------------------- |
|      |                                              |

The first argument of the  `apply()` method is the `cat` object, therefore, the `this` object in the `say()`function is set to the `cat` object. The second argument is an array argument as indicated by th square brackets `[]`

If you pass the `dog` object, the `this` in the `say()` function will set to `dog`. See the following example:

| 123  | say.apply(dog,['Hi']);// Hi// Dog says Woof |
| ---- | ------------------------------------------- |
|      |                                             |

The output is different because `type` and `sound` are the properties of the `dog` object inside the `say()` function.

The `call()` method is similar to the `apply()` method except that you have to pass the arguments in as individual arguments, for example.

| 123456 | say.call(cat,'Hi');// Hi// Cat says Meowsay.call(dog,'Hi');// Hi// Dog says Woof |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

#### The bind() method

The `bind()` method creates a new function instance whose bound to the object that you pass in later. See the following example.

| 12345 | // cat will say in 5svar sayLater = say.bind(cat,'Hello');setTimeout(sayLater, 5000);// Hello// Cat says Meow |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

How it works.

1. First, call bind method of the say function object and pass in the cat object. The `bind()` method returns a new instance of the function: `sayLater()`
2. Then, pass the function instance to the setTimeout function. After 5s, the `sayLater()` function is executed.

Similarly, you can execute the `say()` whose `this` is bound to the `dog` object as follows:

| 1234 | // dog will say in 3ssetTimeout(say.bind(dog,'Hello'), 3000);// Hello// Dog says Woof |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

If you have to use the `call()` method, you would do it as follows:

| 123  | setTimeout(function(){    say.call(cat,'Hello')},5000); |
| ---- | ------------------------------------------------------- |
|      |                                                         |

### JavaScript function that returns a function

Because a function is an object, you can return a function from a function. The following `compareBy()`function returns a function that compares two objects by a provided property.

| 1234567891011121314 | function compareBy(propName) {    return function (a, b) {        var x = a[propName],            y = b[propName];         if (x > y) {            return 1;        } else if (x < y) {            return -1        } else {            return 0;        }    }} |
| ------------------- | ------------------------------------------------------------ |
|                     |                                                              |

Suppose, we have an array of product objects where each product object has two properties: `name` and `price`.

| 12345 | var products = [    {name: 'iPhone', price: 900},    {name: 'Samsung Galaxy', price: 850},    {name: 'Sony Xperia', price: 700}]; |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

To display the product list in the web console, you use the following function:

| 12345 | function displayProducts(products) {    for (let i = 0; i < products.length; i++) {        console.log(`name: ${products[i].name}, price: ${products[i].price}`);    }} |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

You can sort an array by calling the `sort()` method. The `sort()` method accepts a function that compares two elements of the array as an argument.

For example, you can sort the product list based on name by passing a function returned from the `compareBy()` function as follows:

| 12345678 | console.log('Products sorted by name:');products.sort(compareBy('name'));displayProducts(products); //Products sorted by name://name: Samsung Galaxy, price: 850//name: Sony Xperia, price: 700//name: iPhone, price: 900 |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

Similarly, you can sort the product list by price:

| 1234 | // sort products by priceconsole.log('Products sorted by price:');products.sort(compareBy('price'));displayProducts(products); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Now you should understand that all functions in JavaScript are instances of the Function type like other objects.


## JavaScript Recursive Function

**Summary**: this tutorial shows you how to use recursion technique to develop a JavaScript recursive function, which is a function that calls itself.

### Introduction to the JavaScript recursive function

A recursive [function](http://www.javascripttutorial.net/javascript-function/) is a function that calls itself. We will take the classic factorial function for the demonstration.

in Math, a factorial of a non-negative integer is the product of all positive integer less than or equal to it. The factorial of the integer n is denoted by `n!`

The following formula shows how to calculate the factorial of a non-negative integer `n`:

![JavaScript Recursive Function Factorial](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Recursive-Function-Factorial.png)

For example, the factorial of `5` is calculated as follows:

| 1    | 5! = 5 x 4 x 3 x 2 x 1 = 120 |
| ---- | ---------------------------- |
|      |                              |

To develop a factorial function in JavaScript, you simply use a [for loop](http://www.javascripttutorial.net/javascript-for-loop/) as follows:

| 1234567 | function factorial(n) {    var result = 1;    for (let i = n; i > 1; i--) {        result *= i;    }    return result;} |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

This function is clean and readable enough.

However, it is more readable if you develop the factorial function using the recursion technique. See the following recursive factorial function.

| 1234567 | function factorial(n) {    if (n <= 1) {        return 1;    } else {        return n * factorial(n - 1);    }} |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

This is how it works. If `n` is equal to one or zero, the factorial of `n` is `1`; otherwise, the factorial of `n`is the product of `n` and factorial of `n - 1`.

The function seems to work fine initially. However, as mentioned in the [Function type](http://www.javascripttutorial.net/javascript-function-type/) tutorial, the name of a function is a pointer pointing to the function object.

The following code causes an error.

| 123  | var fac = factorial;factorial = null;console.log(fac(5)); // TypeError: factorial is not a function |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

How the script works.

- First, assign the variable named  `fac` to the `factorial` function name.
- Second, set the `factorial` pointer to null.
- Third, call the  `fac` function.

Because inside the function, we referenced to the `factorial` name which was set to [null](http://www.javascripttutorial.net/javascript-data-types/#null) at the time of calling the function, therefore we got a `TypeError` error.

To resolve it, you can use a *named function expression* as follows:

| 1234567 | var factorial = function pf(n) {    if (n <= 1) {        return 1;    } else {        return n * pf(n - 1);    }}; |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

In this case, the  `pf` function name is visible inside the function itself and it remains the same if you assign the function to another variable. As the result, the recursive call will work correctly.

| 123  | var fac = factorial;factorial = null;console.log(fac(5)); // 120 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

In this tutorial, we have shown you how to develop JavaScript recursive functions by implementing the factorial calculation function.

## JavaScript Closure

**Summary**: in this tutorial, you will learn about JavaScript closure and how to use closures in your code more effectively.

### Introduction to JavaScript closure

In JavaScript, a closure is a [function](http://www.javascripttutorial.net/javascript-function/) that is able to remember and access its lexical scope when that function is executing outside its lexical scope.

To understand the closure concept, you need to understand the lexical scoping in first.

#### Lexical scoping

JavaScript defines the scope of a [variable](http://www.javascripttutorial.net/javascript-variables/) by the position of the variable in the source code. In addition, a nested function can have access to the variables declared in its outer scope. This is called lexical scoping.

Consider the following example:

| 12345678910 | function greeting() {    var message = 'Hi';     function sayHi() {        alert(message);    }     sayHi();}greeting(); |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

The `greeting()` function creates a local variable named `message` and a function named `sayHi()`. The `sayHi()` is an inner function that is available only within the body of the `greeting()` function.

The `sayHi()` function has access to the variables of the outer function, therefore, it can access the `message` variable of the `greeting()` function.

Inside the `greeting()` function, we call the `sayHi()` function.

Finally, we call the `greeting()` function. And if you execute the code, it displays the `Hi` message as expected.

#### JavaScript closure

Let’s change the `greeting()` function.

| 1234567891011 | function greeting() {    var message = 'Hi';     function sayHi() {        alert(message);    }     return sayHi;}var hi = greeting();hi(); // still can access the message variable |
| ------------- | ------------------------------------------------------------ |
|               |                                                              |

Now, instead of executing the `sayHi()` function inside the `greeting()` function, the `greeting()`function returns the `sayHi` function object.

Outside of the `greeting()` function, we assign the `hi` variable to the value returned by the `greeting()` function, which is a reference to the `sayHi()` function.

Then we execute the sayHi() function using the reference of that function: `hi()`. If you run the code, you will get the same effect as the one above.

However, the interesting part here is that, normally, a local variable only exists in the duration when the function executes. It means that when the `greeting()` function has completed executing on line 10, the `message` variable is no longer accessible.

But, in this case on line 11, we execute the `hi()` function that reference to the `sayHi()` function, the `message` variable still exists.

The magic of this is the closure. In other words, the `sayHi` function is a closure.

A closure consists of two parts: a function and the ability to remember its lexical scope even when that function executes outside its lexical scope.

#### More JavaScript closure example

The following example illustrates a more practical example of closure.

| 12345678910 | function greeting(message) {   return function(name){        return message + ' ' + name;   }}var sayHi = greeting('Hi');var sayHello = greeting('Hello'); console.log(sayHi('John')); // Hi Johnconsole.log(sayHello('John')); // Hello John |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

The `greeting()` function takes one argument named message and return a function that takes a single argument named `name`. The returned function returns a greeting message that is the combination of the `message` and `name` variables.

The `greeting()` function is like a function factory. It creates `sayHi()` and `sayHello()` functions with the respective messages `Hi` and `Hello`.

The `sayHi()` and `sayHello()` are closures. They share the same function body but store different scopes. In the `sayHi()` closure, the `message` is `Hi`, and in the `sayHello()` closure the `message` is `Hello`.

### JavaScript closure in a loop

See the following HTML page.
```js
| 123456789101112131415 | <!DOCTYPE html><html lang="en"><head>    <meta charset="UTF-8">    <title>JavaScript Closure in a Loop Demo</title></head><body><ul>    <li><a href="#" id="link_1">Link #1</a></li>    <li><a href="#" id="link_2">Link #2</a></li>    <li><a href="#" id="link_3">Link #3</a></li></ul><script src="js/closure-in-loop.js"></script></body></html> |
| --------------------- | ------------------------------------------------------------ |
|                       |                                                              |
```
In this example, we have three links on the page. Suppose when you click a link, the script needs to show you a message to inform you which link you have been clicked.

The code in the `closure-in-loop.js` script file is as follows:
```js
| 1234567891011121314 | function handleClick() {    // get all links    var links = document.getElementsByTagName('a');     // get link count    var linkCount = links.length;    for (var i = 0; i < linkCount; i++) {        links[i].addEventListener('click', function (e) {            alert('You have clicked the link ' + (i + 1));        }, false);    }} handleClick(); |
| ------------------- | ------------------------------------------------------------ |
|                     |                                                              |
```
If you launch the page and click any link, you will get the same message that:

`You have clicked the link 4`

which is not what you expected.

Let’s explain why we have the number 4 in the output.

The condition of the loop is  `i < linkCount` i.e., `3` in this case. In the body of the loop, we increment  `i` by 1 and concatenate the result with a string `'You have clicked the link '`. Therefore the final value of   `i + 1` reflects in the output.

What we are trying to do in the loop is to copy the value of  `i` in each iteration at the time of iteration. However, it did not work as expected. The reason is that the functions assigned to `click `are closures, each closure created in each loop iteration. However, all three closures share the same lexical scope of the `handleClick()` function; in fact, there is just one `i` in the shared scope.

What we need is a new closure scope for each iteration of the loop.

#### Using IIFE solution

To solve this issue, you can use an immediately-invoked function expression (or IIFE) because IIFE creates a scope by declaring a function and immediately execute it.
```js
| 123456789101112131415 | function handleClick() {    // get all links    var links = document.getElementsByTagName('a');    // get link count    var linkCount = links.length;    for (var i = 0; i < linkCount; i++) {        (function (index) {            links[index].addEventListener('click', function (e) {                alert('You have clicked the link ' + (index + 1));            }, false);         })(i);    }}handleClick(); |
| --------------------- | ------------------------------------------------------------ |
|                       |                                                              |
```
#### Using `let` in ES6

As you know that in ES6, you can use the [`let`](http://www.javascripttutorial.net/javascript-variables/#let) keyword to declare a variable that is block scoped. If you use the let keyword inside the [for-loop](http://www.javascripttutorial.net/javascript-for-loop/), JavaScript will declare the variable not just one for the loop, but each iteration.
```js
| 123456789101112 | function handleClick() {    // get all links    var links = document.getElementsByTagName('a');    // get link count    var linkCount = links.length;    for (let i = 0; i < linkCount; i++) {        links[i].addEventListener('click', function (e) {            alert('You have clicked the link ' + (i + 1));        }, false);    }}handleClick(); |
| --------------- | ------------------------------------------------------------ |
|                 |                                                              |
```
Now you should have a good understanding of JavaScript closure and how to closures in code more effectively.

## JavaScript Passing By Value

### Understanding JavaScript Pass By Value

**Summary**: this tutorial explains how JavaScript pass by value works and gives you some examples of passing primitive and reference variables to a function.

Before going forward with this tutorial, you should have good knowlege of the[ primitive and reference values, and the differences between them](http://www.javascripttutorial.net/javascript-primitive-vs-reference-values/).

### JavaScript pass by value or pass by reference

In JavaScript, all [function](http://www.javascripttutorial.net/javascript-function/) arguments are *always* passed by value. It means that JavaScript copies values of the [variables](http://www.javascripttutorial.net/javascript-variables/) that you pass to a function into local variables. Any changes that you make to the local variables inside the function does not affect the arguments that you passed in. In other words, the changes to the arguments are not reflected outside the function.

If function arguments are passed by reference, the changes of variables that you pass to the function will be reflected outside the function. This is impossible in JavaScript.

### Passing by value of primitives values

Let’s take a look at the following example.

| 123456 | function square(x) {    x = x * x;}var y = 10;square(y);console.log(y); // -- no change |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

How the script works.

First, define a `square()` function that has an argument x .The function changes the value of the `x` argument.

Next, declare and initialize the variable y a value of 10.

![JavaScript Pass By Value - declare variable](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Pass-By-Value-declare-variable.png)

Then, pass the `y` variable to the `square()` function. When passing the variable `y` to the `square()`function, JavaScript copies the value of `y` to the `x` variable.

![JavaScript Pass By Value - passing primitive argument](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Pass-By-Value-passing-primitive-argument.png)

After that, the `square()` function changes the x variable. However, it does not change the value of the variable `y`. This is because `x` and `y` are totally different variables.

![JavaScript Pass By Value - changing primitive value](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Pass-By-Value-changing-primitive-value.png)

Finally, the value of the `y` value does not change after the `square()` function completes.

![JavaScript Pass By Value - primitive type](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Pass-By-Value-primitive-type.png)

If JavaScript were passed by reference, the value of the variable `y` would change to `100`.

### Passing by value of references

It’s obvious to see that primitive values are passed by values. However, it is not the case for the reference values. Take this for example:

| 12345678910 | function turnOn(machine) {    machine.isOn = true;} var computer = {    isOn: false}; turnOn(computer);console.log(computer.isOn); // true; |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

How the script works.

First, define the `turnOn()` function that accepts an object `machine`. The function sets the `isOn`property of the object to `true`.

Next, declare a variable `computer` and assign it an object whose `isOn` property is set to `false`. Internally, the `computer` contains a reference  value which essentially is a pointer that points to an object as illustrated below:

![JavaScript Pass By Value - Object Declaration](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Pass-By-Value-Object-Declaration.png)

Then, pass the `computer` variable to the `turnOn()` function. JavaScript copies the value of the `computer` variable to `machine` variable. As the result, both `computer` and `machine` variables are pointing to the same object as shown below:

![JavaScript Pass By Value -Passing argument](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Pass-By-Value-Passing-argument.png)

After that, inside the `turnOn()` function, the `isOn` property of the object is set to `false` via the `machine` reference.

![JavaScript Pass By Value - changes](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Pass-By-Value-changes.png)

Finally, accessing the `isOn` property of the `computer` object returns `true`.

![JavaScript Pass By Value - accessing outside function](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Pass-By-Value-accessing-outside-function.png)

It seems that a reference value is passed to the function by reference. However, this is not the case.

In fact, when you pass a reference value to a function, you are passing the reference to the object, not the object. Therefore, the function can modify the properties of the object.

In addition, when you pass a reference to a function, the function cannot change the reference to point to another object.

Let’s prove it through the following example.

| 1234567891011 | function turnOn(machine) {    machine = {        isOn: true    };} var computer = {    isOn: false}; console.log(computer.isOn); // false; |
| ------------- | ------------------------------------------------------------ |
|               |                                                              |

This time, the `turnOn()` function change the `machine` object so that it points to another new object.

Before passing the `computer` object to the `turnOn()` function, the `isOn` property of the `computer`object is `false`.

If the `computer` variable was passed by reference, the `computer` variable would be changed to point to the new object whose `isOn` property is `true`.

However, when we access the `isOn` property again, its values is `false`, showing that the original reference did not change even though the argument value changed inside the function.

Now, you should understand that all function arguments in JavaScript are passed by value, not by reference.