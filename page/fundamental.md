---
sidebar: auto
---

# Javascript Fundamental

## JavaScript Syntax

**Summary**: in this tutorial, you will learn about JavaScript syntax including case-sensitivity, identifiers, comments and statements.

### JavaScript is case-sensitive

Everything in JavaScript including [variables](http://www.javascripttutorial.net/javascript-variables/), [function](http://www.javascripttutorial.net/javascript-function/) names, [class](http://www.javascripttutorial.net/es6/javascript-class/) names, and operators are case-sensitive. It means that `counter` and `Counter` variables are different.

Likewise, you cannot use  `instanceof` as a name of a function because it is a keyword. However, `instanceOf` is a valid function name.

### Identifiers

An identifier is the name of a variable, function, parameter, or class. An identifier consists of one or more characters in the following format:

- The first character must be a letter (a-z, or A-Z), an underscore(_), or a dollar sign ($).
- The other characters can be letters (a-z, A-Z), numbers (0-9), underscores (_) and dollar signs ($).

Note that the letter in this context is not limited to the ASCII character but may include extended ASCII or Unicode though it is not recommended.

It is a good practice to use camel case for the identifiers, meaning that the first letter is lowercase, and each additional word starts with a capital letter.

For example, the following names are identifiers:

```
1   hello
2   world
3   jaaa
```


### Comments

JavaScript supports both single-line and block comments. A single-line comment starts with two forward-slash characters (//), for example:

```js
 1     // this is a single-line comment
```

A block comment starts with a forward slash and asterisk (/*) and ends with the opposite (*/) as shown in the following example.
```js
1   /*
2   * This is a block comment that can
3   * span multiple lines
4   */                                                       
```

It is a good practice use an asterisk to begin the comment line for readability purpose.

### Statements

Although JavaScript does not require to end a statement with a semicolon (;), it is recommended to always use the semicolon to end a statement.

The reason is that the semicolon will make your code more readable and helps you avoid many issues that you may encounter. In addition, you may need to combine and compress the JavaScript code before deploying it to the production environment to remove extra white space to save the bandwidth; without the semicolons, you will have the syntax errors.
```js
1     var a = 10;
2     var b = 20;
```

You can use a code block that begins with left curly brace ({) and ends with the right curly brace (}) to combine multiple statements as follows:
```js
1   if( a > b) {   
2       console.log('a is greater than b');
3       return 1;
4   } 
```

### Keywords

JavaScript defines a list of keywords that have special uses. You cannot use the keywords as the identifiers. The list of complete list of JavaScript keywords is as follows:

| `break`    | `export`     | `super`  |
| ---------- | ------------ | -------- |
| `case`     | `extends`    | `switch` |
| `catch`    | `finally`    | `typeof` |
| `class`    | `for`        | `this`   |
| `const`    | `function`   | `throw`  |
| `continue` | `if`         | `try`    |
| `debugger` | `import`     | `var`    |
| `default`  | `in`         | `void`   |
| `delete`   | `instanceof` | `while`  |
| `do`       | `new`        | `with`   |
| `else`     | `return`     | `yield`  |

Now you should have a good understanding of the JavaScript syntax including naming an identifier, constructing statements, and making comments in code.

## JavaScript Variables

**Summary**: in this tutorial, we will discuss JavaScript variables and show you various ways to declare the variables in JavaScript.

JavaScript variables are loosely typed, that is to say, a variable can hold a value with any [type](http://www.javascripttutorial.net/javascript-data-types/) of data. A variable is just a named placeholder for a value.

### Declare JavaScript variables using `var` keyword

To declare a variable, you use the `var` keyword followed by the variable name as follows:
```js
1   var foo;
```

A variable name can be any valid [identifier](http://www.javascripttutorial.net/javascript-syntax/#identifiers). The `foo` variable is declared and hold a special value [`undefined`](http://www.javascripttutorial.net/javascript-data-types/#undefined).

After declaring a variable, you can assign the variable a value as follows:

```js
1   foo = "Hello"; 
```
To declare a variable and initialize it at the same time, you use the following syntax:
```js
1   var variable_name = value;
```

For example, the following statement declares the `foo` variable and assign it a value `"Hello"`
```js
1   var foo = "Hello";
```

You can declare two or more variables using one statement, each variable declaration is separated by a comma (,) as follows:

```js
1   var foo = "Hello",
2   bar = 100;
```

As mentioned earlier, you can store a number in the `foo` variable as the following example though it is not recommended.
```js
1   foo = 100;
```
### Undefined vs. undeclared variables

It’s important to distinguish between undefined and undeclared variables.

An undefined variable is a variable that has been declared. Because we have not assigned it a value, the variable used the `undefined` as its initial value. In contrast, an undeclared variable is the one that has not been declared in the accessible scope.

See the following script.

```js
var foo;
 
console.log(foo); // undefined
console.log(bar); // ReferenceError: bar is not defined
```

The `foo` variable is declared but not initialized therefore its value is undefined whereas the `bar`variable has not been declared hence accessing it causes a `ReferenceError`.

### Global and local variables

In JavaScript, all variables exist within a scope that determines the lifetime of the variables and which part of the code can access them.

JavaScript mainly has global and function scopes. (ES6 introduced a new scope called [block scope](http://www.javascripttutorial.net/es6/javascript-let/)).

If you declare a variable in a [function](http://www.javascripttutorial.net/javascript-function/), JavaScript adds the variable to the function scope. In case you declare a variable outside of a function, JavaScript adds it the global scope.

In JavaScript, you define a function as follows:

```js
1   function function_name() {
2     // logic
3   }
```

and call the function using the following syntax:
```js
1   function_name(); 
```

You will learn more about function in more detail in [function tutorial](http://www.javascripttutorial.net/javascript-function/).

The following example defines a function named `say` that has a local variable named `message`.
```js
1   function say(){
2       var message = "Hi";
3   } 

```

The `message` variable is a local variable. In other words, it only exists inside the function. If you try to access it outside the function as follows:

```js
1   function say() {
2       var message = 'Hi';
3   }
4   console.log(message); // ReferenceError
```

You will get a `ReferenceError` because the `message` variable was not defined.

### Variable shadowing

See the following example.

```js
1   // global variable
2   var message = "Hello";
3   function say() {   
4       // local variable     
5       var message = 'Hi';
6       console.log(message);   // which message?
7   }
8   say();  // Hi
9   console.log(message);   // Hello 
```

In this example, we have two variables that share the same name: `message`. The first `message` variable is a global variable whereas the second one is the local variable.

Inside the `say()` function, the global message variable is shadowed. It cannot be accessible inside the `say()` function but outside of the function. This is called variable shadowing.

### Accessing global variable inside the function

See the following example.
```js
1   // global variable
2   var message = "Hello";
3   function say() {    
4       // local variable
5       message = 'Hi';
6       console.log(message);// which message?
7   }
8   say(); // Hi
9   console.log(message);  // Hi
```

In this example, we define a global variable named `message`. In the `say()` function, we reference the global `message` variable by omitting the `var` keyword and change its value to a string of `Hi`.

Although it is possible to refer to a global variable inside a function, it is not recommended. This is because the global variables are very difficult to maintain and potentially cause many confusions.

### Non-strict mode

The following example defines a function and declares a variable `message`. However, the `var` keyword is not used.

```js
1function say() {
2message = 'Hi'; // what?
3console.log(message);
4}
5say(); // Hi
6console.log(message); // Hi 
```

When you execute the script, it outputs the  `Hi` string twice in the web console.

Why?

Because when we call the `say()` function, the JavaScript engine looks for the variable named `message`inside the scope of the function. As the result, it could not find any variable declared with that name so it goes up to the next immediate scope which is the global scope in this case and asks whether or not the `message` variable has been declared.

Because the JavaScript engine couldn’t find any of global variable named `message` so it creates a new variable with that name and adds it to the global scope.

### strict mode

To avoid creating a global variable accidentally inside the function because of omitting the `var`keyword, you use the strict mode by adding the `"use strict";` at the beginning of a JavaScript file (or a function) as follows:

```js
1   "use strict";
2
3   function say() {
4       message = 'Hi'; // ReferenceError
5       console.log(message);
6   }
7   say(); // Hi
8   console.log(message);// Hi
```

From now on, you should always use the strict mode in your JavaScript code to eliminate some JavaScript silent errors and make your code run faster.

### JavaScript variable hoisting

Hosting is the mechanism that JavaScript engine moves all the variable declarations to the top of their scope, either function or global scope.

If you declare a variable with var keyword, the variable is hoisted to the top of its enclosing scope. As the result, if you access the variable before declaring it, the variable evaluates to `undefined`.

See the following example.

```js
1   console.log(foo); // undefinedvar 
2   foo;
```

JavaScript engines move the declaration of the `foo` variable to the top, so it is equivalent to the following script.

```js
1   var foo;
2   console.log(foo);// undefined
```

If there were no hoisting, you would get a `ReferenceError` because you referenced to a variable that was not defined.

See another example.

```js
1   console.log(baz);
2   var baz = 'baz';
```
JavaScript engine moves only the declaration of the variables to the top. However, it keeps the initial assignment of the variable remain intact. As the result, the code above is equivalent to the following:

```js
1   var baz;
2   console.log(baz);
3   // undefinedbaz = 'baz';
```

### Using `let` and `const` keywords

From ES6, you can use the `let` keyword to declare a variable. The `let `keyword is similar to the `var`keyword. However, variable declared using the `let` keyword is block-scoped, not function-scoped.

In the following example, we declare the `tmp` variable within a block surrounding by the curly braces `{}`. The  `tmp` variable only exists inside the block, therefore, any reference to it outside of the block will cause a `ReferenceError`.

```js
1   var foo = 20, bar = 10; 
2
3   {
4       let tmp = foo;
5       foo = bar;
6       bar = tmp;
7   }
8
9   console.log(tmp); // ReferenceError
```

The `const` keyword works like the `let` keyword, but the variable that you declare must be initialized immediately with a value, and that value can’t be changed afterward.
```js
1   const CODE = 100;
2   CODE = 200; // TypeError: `CODE` is read-only
```

We will discuss more pitfalls of the `const` in the JavaScript object tutorial.

Now you should have a good understanding of how the JavaScript variable works.

## JavaScript Data Types

**Summary**: in this tutorial, you will learn about the JavaScript data types and their unique characteristics.

JavaScript has six primitive data types:

1. [`null`](http://www.javascripttutorial.net/javascript-data-types/#null)
2. [`undefined`](http://www.javascripttutorial.net/javascript-data-types/#undefined)
3. [`boolean`](http://www.javascripttutorial.net/javascript-data-types/#boolean)
4. [`number`](http://www.javascripttutorial.net/javascript-data-types/#number)
5. [`string`](http://www.javascripttutorial.net/javascript-data-types/#string)
6. [`symbol`](http://www.javascripttutorial.net/javascript-data-types/#symbol) – available only from ES6

and one complex data type called [`object`](http://www.javascripttutorial.net/javascript-data-types/#object).

JavaScript is a dynamic language or loosely typed therefore a [variable](http://www.javascripttutorial.net/javascript-variables/) does not associate with any type, however, its value does. In other words, the same variable can hold values of different types at any time.

```js
1   var foo = 120; // foo is a number
2   foo = false;   // foo is now a boolean
3   foo = "foo";   // foo is now a string
```

To get the current value of a variable, you use the  `typeof` operator.

### The undefined type

The `undefined` type is a primitive type that has one special value `undefined`. By default, when a variable is declared but not initialized, it is assigned the value of `undefined`.

Consider the following example.
```js
1   var foo;
2   console.log(foo);        // undefined
3   console.log(typeof foo); // undefined
```

`foo` is a variable. Because it is not initialized therefore it is assigned the undefined value. The type of `foo` is also `undefined`.

It is confusing that the  `typeof` operator also returns `undefined` when you call it on a variable that has not been declared as follows:
```js
1   console.log(typeof bar); // undefined
```

### The null type

The `null` type is the second primitive data type that has only one value: `null`. Javascript defines that `null` is an empty object pointer.

See the following example.

```js
1   var obj = null;
2   console.log(typeof obj); // object
```

It is a good practice to assign a variable that later holds an object to `null` so that you can check whether the object is `null` or not by using the [if statement](http://www.javascripttutorial.net/javascript-if-else/) as follows:

```js
1   if(obj != null) {
2   // call method of the object
3   }
```

JavaScript defines that `null` is equal to `undefined` as shown in the following statement.
```js
1   console.log(null == undefined); // true
```

### The number type

JavaScript uses the [IEEE-754 format](https://en.wikipedia.org/wiki/IEEE_floating_point) to represent both integer and floating-point numbers.

#### Integer numbers

The following statement declares a variable that holds an integer.
```js
1   var num = 100;
```

If you want to represent the octal (base 8) literals, you put the first digit as zero (0) followed by octal digit numbers (0 to 7) as follows:
```js
1   var oct = 060; // octal for 48 
```

If the literal of an octal number is out of the range, JavaScript treats it as a decimal as shown in the following example.
```js
1   var d = 090; // intepreted as 90
```

To create hexadecimal (base 16) literal, you must use `0x` (in lowercase) as the first two characters followed by any number of hexadecimal digits (0 to 9, and A to F).
```js
1    var h = 0xf; // same as 0xF hexadecimal for 15
```

#### Floating-point numbers

To represent a floating-point number, you include a decimal point followed by at least one number. See the following example:

```js
1   var f1 = 12.5;
2   var f2 = .3;   // same as 0.3, also valid but not recommended   
```

JavaScript converts a floating-point number into an integer number if the number appears to be the whole number. The reason is that Javascript always wants to use less the memory since a floating-point value uses twice as much memory as an integer value.

```js
1   var f3 = 200.00; // interpreted as integer 200
```

JavaScript allows you to use the e-notation to represent very large or small numbers as in the following example.
```js
1   var f4 = 2.17e6; // ~ 2170000
```

JavaScript provides the minimum and maximum values of a number that you can access using `Number.MIN_VALUE` and `Number.MAX_VALUE`. In addition, JavaScript uses `Infinity` and `-Infinity` to represent the finite numbers, both positive and negative.

See the following example.

```js
1   console.log(Number.MAX_VALUE); // 1.7976931348623157e+308
2   console.log(Number.MIN_VALUE); // 5e-324
3   console.log(Number.MAX_VALUE + Number.MAX_VALUE); // Infinity
4   console.log(-Number.MAX_VALUE - Number.MAX_VALUE); // -Infinity
```

#### NaN

JavaScript has a special numeric value called `NaN`, which stands for Not a Number. In fact, it means an invalid number.

For example, the division of a string by a number returns `NaN` as in the following example.

1   console.log('a'/2); // NaN;

The `NaN` has two special characteristics:

1. Any operation with `NaN` returns `NaN`.
2. The `NaN` does not equal any value, including itself.

Here are some examples.
```js
1   console.log(NaN/2); // NaN
2   console.log(NaN == NaN); // false
```

### The string type

In JavaScript, a string is a sequence of zero or more characters. A literal string begins and ends with either single quote(‘) or double quotes (“).  A key point to remember is that a string that begins with a double quote must end with a double quote and a string that begins with a single quote must end with a single quote.

Here are some examples:

```js
1   var greeting = 'Hi';
2   var foo = "It's a valid string";
3   var bar = 'I'm also a string';
```

JavaScript strings are immutable. It means that you cannot modify a string once it is created. However, you can create a new string based on an operation on the original string, like this:

```js
1   var foo = 'JavaScript';
2   foo = foo + ' String';
```

First, we declare the `foo` variable and initialize it to a string of `'JavaScript'`. Second, on the next line, we use the `+` operator to combine `'JavaScript'` with `' String'` to make its value as `'Javascript String'`.

Behind the scene, JavaScript engine creates a new string that holds the new string `'JavaScript String'`and destroys two other original strings `'JavaScript'` and `' String'`.

### The boolean type

The `boolean` type has two values: `true` and `false`, in lowercase. The following examples declare two variables that hold boolean values.

```js
1   var inProgress = true;
2   var done = false;
3   console.log(typeof done); // boolean
```

JavaScript allows values of other types to be converted into boolean values of `true` or `false`.

To convert a value of another data type into a boolean value, you use the [`Boolean`](http://www.javascripttutorial.net/javascript-boolean/) function. The following table shows the conversion rules:

| Type      | true                         | false        |
| --------- | ---------------------------- | ------------ |
| string    | non-empty string             | empty string |
| number    | non-zero number and Infinity | 0, NaN       |
| object    | non-null object              | null         |
| undefined |                              | undefined    |

See the following demonstration.

```js
1   console.log(Boolean('Hi'));// true
2   console.log(Boolean(''));  // false
3
4   console.log(Boolean(20));  // true
5   console.log(Boolean(Infinity));  // true
6   console.log(Boolean(0));  // false
7
8   console.log(Boolean({foo: 100}));  // true on non-empty object
9   console.log(Boolean(null));// false 
```

### The symbol type

JavaScript has a new primitive type in ES6: the `symbol`. Different from other primitive types, the `symbol`type does not have a literal form.

To create a symbol, you call the `Symbol` function as follows:
```js
1   var s1 = Symbol(); 
```

Note that `Symbol` is a function, not an object constructor, therefore, you cannot use the `new` operator. If you do so, you will get a `TypeError`.

The `Symbol` function creates a new unique value every time you call it.

```js
1   console.log(Symbol() == Symbol()); // false
```

You can pass a descriptive string to the `Symbol` function for the logging and debugging purposes.

```js
1   var s2 = Symbol('event.save');
```

When you call the `toString()` method on the symbol variable, it returns more descriptive name as shown below:

```js
1   console.log(s2.toString()); // Symbol(event.save)
```

You can use symbols for many purposes. One of them is to create a string-like constant that can’t clash with any other value. The following example creates a symbol that represents the click event.

```js
1   const CLICK = Symbol('click');
```

The string ‘click’ may be used for different purposes and not unique. However, the `CLICK` symbol is.

### The object type

In JavaScript, an object is a collection of properties, where each property is defined as a key-value pair. The following example defines an empty object using the object literal form:

```js
1   var emptyObject = {};
```

The following example defines the `person` object with two properties:

```js
1   var person = {
2       firstName: 'John',
3       lastName: 'Doe'
4   };
```

A property name of an object can by any string. You can use quotes around the property name if it is not valid [JavaScript identifier](http://www.javascripttutorial.net/javascript-variables/#identifiers).

For example, if you have a property `first-name`, you must use the quotes such as `"first-name",b`ut `firstName` is a valid JavaScript identifier so the quotes are optional.

If you have more than one property, you use commas (,) to separate the pairs.

JavaScript allows you to nest object as in the following example.

```js
1   var contact = {
2       firstName: 'John',
3       lastName: 'Doe',
4       email: 'john.doe@example.com',
5       phone: '(408)-555-9999',
6       address: {        
7           building: '4000',
8           street: 'North 1st street',
9           city: 'San Jose',
10          state: 'CA',
11          country: 'USA'
12      }
13  }
```

The `contact` object consists of `firstName`, `lastName`, `email`, `phone`, and `address` properties. The `address` property itself is also an object that consists of `building`,  `street`, `city`, `state`, and `country` properties.

You can access properties of an object by using two notations: the dot notation (.) and array-like notation ([]).

The following example uses the dot notation (.) to access the `firstName` and `lastName` properties of the contact object.

```js
1   console.log(contact.firstName);
2   console.log(contact.lastName); 
```

To get a property of a nested object, you use the following form.

```js
1   console.log(contact.address.country);
```

If you refer to a non-existent property, you will get an `undefined` value as follows:

```js
1   console.log(contact.age); // undefined
```

The following example uses the array-like notation to access the `email` and `phone` properties of the `contact` object.

```js
1   console.log(contact[phone]);   // '(408)-555-9999'
2   console.log(contact[email]);   // 'john.doe@example.com'
```

Besides the object literal form, you can use the `new` keyword to create a new object as follows:

```js
1   var customer = new Object();
```

And assign the property of the object a value:

```js
1   customer.name = 'ABC Inc.';
```

In JavaScript, all objects are derived from the `Object` type. We will discuss more the `Object` type in the next tutorial.

In this tutorial, you have learned about the primitive JavaScript data types including undefined, null, number, string, boolean, symbol, and object.

## JavaScript Primitive vs. Reference Values

**Summary**: in this tutorial, you will learn the differences between primitive and reference values.

### Accessing by value or by reference

In JavaScript, a [variable](http://www.javascripttutorial.net/javascript-variables/) may store two [types of data](http://www.javascripttutorial.net/javascript-data-types/): primitive and reference. JavaScript provides six primitive types as `undefined`, `null`, `boolean`, `number`, `string`, and `symbol` , and a reference type `object`.

When you assign a variable a value, the JavaScript engine must determine whether the value is a primitive or a reference value.

If the variable stores a primitive value, when you manipulate its value, you are working on the actual value stored in the variable. In other words, the variable that stores a primitive value is accessed *by value*.

Unlike the primitive value, when you manipulate an object, you are working on the *reference* to that object, rather than the actual object. In short, a variable that stores an object is accessed *by reference*.

### Copying primitive values

When you assign a variable that stores a primitive value to another, the value stored in the variable is created and copied into the new variable.

Let’s take a look at the following example.

First, declare a variable a and initialize its value to 10.

1   var a = 10;

![JavaScript Primitive Value Example](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Primitive-Value-Example.png)

Second, declare another variable `b` and assign it a value of the variable `a`. Internally, JavaScript engine copies the value stored in  `a` into the location of `b`.

1   var b = a;

![JavaScript Primitive Value Copying](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Primitive-Value-Copying.png)

Third, assign the variable `a` new value 10.

![JavaScript Primitive Value Assigning](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Primitive-Value-Assigning.png)

Because a and b have no relationship, therefore when you change the value stored in the `b` variable, the value of the `a `variable remains intact.

```js
1   console.log(a);    // 10;
2   console.log(b);    // 20;
```

### Copying reference values

When you assign a reference value from one variable to another, the value stored in the variable is also copied into the location of the new variable. The difference is that the values stored in both variables now are the address of the actual object stored in the heap. As the result, both variables are pointing to the same object.

Here is an example.

First, declare a variable `x` that holds an object whose name property is `'John'`.

```js
1   var x = {name: 'John'};
```

![JavaScript Reference Declaration](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Reference-Declaration.png)

Second, declare another variable y and assign the `x` variable to `y`. both x and y are now pointing to the same object in the heap.

```js
1   var y = x;
```

![JavaScript Reference Assignment](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Reference-Assignment.png)

Third, modify the value stored in the `name` property of the object using the `y` variable.

```js
1   y.name = 'David'; 
```

![JavaScript Reference Modifying Property](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Reference-Modifying-Property.png)

Because both x and y are pointing to the same object, therefore the change is also reflected if you access the object using the `x` variable.
```js
1   console.log(x.name); // 'David'
```

![JavaScript Reference Accessing Property](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Reference-Accessing-Property.png)

In this tutorial, you have learned about accessing by value and by reference, and also the differences between them.

## JavaScript Boolean vs. boolean

**Summary**: in this tutorial, we will introduce you to the JavaScript `Boolean` object and show you the differences between the `Boolean` object and the `boolean` primitive type.

### JavaScript boolean primitive type

JavaScript provides a [boolean](http://www.javascripttutorial.net/javascript-data-types/#boolean) primitive type that has two values of `true` and `false`. The following example declares two [variables](http://www.javascripttutorial.net/javascript-variables/) that hold boolean values of `false` and `true`:

```js
1   var isPending = false;
2   var isDone = true;
```

When you apply the  `typeof` operator to a variable that holds primitive boolean value, you get the `boolean` as the following example:

```js
1   console.log(typeof(isPending));    //  boolean
2   console.log(typeof(isDone)); // boolean 
```

### JavaScript Boolean object

In addition to the `boolean` primitive type, JavaScript also provides you with the global `Boolean()` function, with the letter `B` in uppercase, to cast a value of another type to `boolean.`

The following example shows you how to use the `Boolean()` function to convert a string into a boolean value. Because the string is not empty, therefore it returns true.

```js
1   var a = Boolean('Hi');
2   console.log(a); // true
3   console.log(typeof(a)); // boolean  
```

The `Boolean` is also a wrapper object of the `boolean` primitive type. It means that when you use the Boolean constructor and pass in either `true` or `false`, you create a Boolean object.
```js
1   var b = new Boolean(false);
```

To get the primitive value back, you call the `valueOf()` method of the Boolean object as follows:

```js
1   console.log(b.valueOf()); // false
```

However, if you call the `toString()` method of a Boolean object, you get a string value `"true"` or `"false"`. See the following example.

```js
1   console.log(b.toString()); // "false"
```
### JavaScript boolean vs. Boolean

Consider this example.

```js
1   var foo = true;
2   var bar  = new Boolean(false);
```

First, because `bar` is an object, you can add a property to the `bar` object as follows:

```js
1   bar.primitiveValue = bar.valueOf();
2   console.log(b.primitiveValue); // false
```

However, you cannot do it with the primitive boolean variable like the `foo` variable:

```js
1   foo.name = 'primitive';
2   console.log(foo.name); // undefined
```

Second, the  `typeof` of Boolean object returns `object`, whereas the  `typeof` of a primitive boolean value returns `boolean`.

```js
1   console.log(typeof foo); // boolean
2   console.log(typeof bar); // object
```

Third, when applying the  `instanceof` operator to a Boolean object, it returns `true`. However, it returns `false` if you apply the  `instanceof` operator to a boolean value.

```js
1   console.log(foo instanceof Boolean); // false
2   console.log(bar instanceof Boolean); // true
```

It is a good practice to *never* use the `Boolean` object because it will create many confusions especially when you use it in an expression. See the following example.

```js
1   var falseObj = new Boolean(false);
2   if (falseObj) {
3       console.log('weird part of the Boolean object');
4   }    
```

How the script works.

- First, create `falseObj` as a `Boolean` object wrapper for the `false` value.
- Second, use `falseObj` in the  [`if`](http://www.javascripttutorial.net/javascript-if-else/) statement. Because `falseObj` is an object, and JavaScript engine *coerces* it to a boolean value of `true` . As the result, the statement inside the  `if` block is executed.

The following table summarizes the differences between the JavaScript `Boolean` and `boolean`:

| Operator             | boolean | Boolean |
| -------------------- | ------- | ------- |
| `typeof`             | boolean | object  |
| `instanceof` Boolean | false   | true    |

It is recommended that you use the `Boolean()` function to convert a value of a different type to a Boolean type but you should never use the `Boolean` as a wrapper object of a primitive boolean value.

In this tutorial, you have learned about the JavaScript `Boolean` object and the differences between the `Boolean` object and `boolean` primitive type.