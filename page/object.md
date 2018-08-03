---
sidebar: auto
---

# JavaScript Objects

## Understanding JavaScript Objects

**Summary**: in this tutorial, you will learn about JavaScript objects and how to define properties and methods for objects.

### Introduction to JavaScript objects

If you have been working with C++, Java, C#, you typically define a class, which is a blueprint for objects, and then creates multiple objects that have the same properties and methods from the class.

JavaScript approached object-oriented programming differently. It had no concept of classes like other object-oriented programming languages.

JavaScript defines an object as an unordered collection of properties each of which contains a [primitive value](http://www.javascripttutorial.net/javascript-data-types/), an object or a [function](http://www.javascripttutorial.net/javascript-function/). In other words, an object is a group of name-value pairs where value could be data or a function.

An object can be created based on a native type or user-defined type. The easiest way to define a custom object is to create a new instance of `Object` and add properties and methods to it as in the following example.

| 12345678910 | var machine = new Object(); // propertymachine.isOn = false; // methodmachine.start = function() {    this.isOn = true;    console.log('Machine has been starting');} |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

In this example, we define the machine as an instance of  `Object`, and add the `isOn` property and `start()` method to it.

An alternative way, or may be the easier way is to define an object using the object literal form. The following example defines the `machine` object that is equivalent to the `machine` object in the previous example.

| 1234567 | var machine = {    isOn: false,    start: function() {        this.isOn = true;        console.log('Machine has been starting');    }}; |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

### Types of properties

JavaScript specifies the characteristics of properties via internal attributes surrounded by the two pair of square brackets e.g., `[[Enumerable]]`. There are two types of properties: data properties and accessor properties.

#### Data properties

A data property contains a single location for a data value. A data property has four attributes as described below.

-  `[[Configurarable]]` – determines whether a property can be removed via delete or redefined.
-  `[[Enumerable]]` – indicates that the property will be returned in the for-in loop.
-  `[[Writable]]` – indicate that if the value of the property can be changed.
-  `[[Value]]` – contains the actual value of the property. It is the location that the value of the property is read from and written to.

By default, the `[[Configurable]]` , `[[Enumerable]]`, and `[[Writable]]` attributes are set to true for all properties defined directly on an object. The default value of the `[[Value]]` attribute is `undefined`.

To change any attributes of a property, you use the `Object.defineProperty()` method. The `Object.defineProperty()` method accepts three arguments:

- The object.
- The property name of the object.
- The descriptor object that has four properties: `configurable`, `enumerable`, `writable`, and `value`.

If you use the `Object.defineProperty()` method to define a property of the object, the default values of `[[Configurable]]`, `[[Enumerable]]`, and `[[Writable]]` are set to `false` unless otherwise specified.

Let’s take a look some examples to get a better understanding of these attributes.

The following example defines an object machine with the `isOn` property on it.

| 1234 | var machine = {};machine.isOn = false;delete machine.isOn;console.log(machine.isOn); // undefined |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Because by default the `[[Configurable]]` property is set to `true`, we can remove it via the `delete`operator.

The following example creates a `machine` object and adds the `isOn` property to it using the `Object.defineProperty()` method.
```js
| 123456789 | var machine = {}; Object.defineProperty(machine, 'isOn', {    configurable: false,    value: false}); delete machine.isOn; // undefined// Uncaught TypeError: Cannot delete property 'isOn' of #<Object> |
| --------- | ------------------------------------------------------------ |
|           |                                                              |
```

In this example, we set the `configurable` attribute to `false` therefore deleting the `isOn` property in the strict mode causes an error.

In addition, once a property is defined as non-configurable, it cannot become configurable. If you use the `Object.defineProperty()` method to change any attribute other than writable, you will get an error.
```js
| 1234 | Object.defineProperty(machine, 'isOn', {    configurable: true});// Uncaught TypeError: Cannot redefine property: isOn |
| ---- | ------------------------------------------------------------ |
|      |                                                              |
```
By default, the enumerable attribute of all the properties defined on an object are true. It means that you can iterate over the properties using the for-in loop as shown in the following example.
```js
| 12345678910 | var machine = {};machine.isOn = false;machine.name = 'computer'; for (var prop in machine) {    console.log(prop);} // isOn// name |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |
```
The following code makes the name property non-enumerable by setting the enumerable attribute to false.
```js
| 123456789 | // make the name non-enumerableObject.defineProperty(machine, 'name', {    enumerable: false}); for (var prop in machine) {    console.log(prop);}// isOn |
| --------- | ------------------------------------------------------------ |
|           |                                                              |
```
#### Accessor properties

Similar to the data properties, the accessor properties also have `[[Configurable]]` and `[[Enumerable]]` attributes. However, the access properties have the `[[Get]]` and `[[Set]]` attributes instead of `[[Value]]` and `[[Writable]]`.

When you read data from the accessor property, the `[[Get]]` function is called and returned a value. The default returned value of the `[[Get]]` function is `undefined`. Similarly, when you assign the property a value, the `[[Set]]` function is called.

To define an accessor property, you must use the `Object.defineProperty()` method. See the following example.
```js
| 123456789101112131415161718192021222324252627 | var person = {    firstName: 'John',    lastName: 'Doe'} Object.defineProperty(person, 'fullName', {    get: function() {        return this.firstName + ' ' + this.lastName;    },    set: function(value) {        var parts = value.split(' ');        if (parts.length == 2) {            this.firstName = parts[0];            this.lastName = parts[1];        } else {            throw 'Invalid name format';        }    }}); console.log(person.fullName); // person.fullName = 'John Cho'; console.log(person.firstName); // Johnconsole.log(person.lastName); // Choconsole.log(person.fullName); // John Cho |
| --------------------------------------------- | ------------------------------------------------------------ |
|                                               |                                                              |
```
In this example, first, we define the `person` object that contains two properties: `firstName` and `lastName`. Then, we add the `fullName` as the accessor property to the person object as an accessor property.

The `[[Get]]` method returns the full name that is the result of concatenating of `firstName`, `space`, and `lastName`.

The `[[Set]]` method splits the argument by the space character and assigns the `firstName` and `lastName `properties the corresponding parts of the name. If the name is not in the correct forma i.e., first name, space, and lastname,  it will throw an error.

### Defining multiple properties

In ES5, you can define multiple properties in a single statement using the `Object.definedProperties()`method. See the following example.
```js
| 123456789101112131415161718192021 | let product = {}; Object.defineProperties(product, {    name: {        value: 'iPhone'    },    price: {        value: 799    },    tax: {        value: 0.1    },    netPrice: {        get: function() {            return this.price * (1 + this.tax);        }    }}); console.log('The net price of ' + product.name +    ' is ' + product.netPrice.toFixed(2) + ' USD'); |
| --------------------------------- | ------------------------------------------------------------ |
|                                   |                                                              |
```
The code defines three data properties: `name`, `price`, and `tax`, and one accessor property `netPrice`for the `product` object.

### Getting attributes of properties

ES5 had a new method called `Object.getOwnPropertyDescriptor()` that allows you to get the descriptor object of a property.

The `Object.getOwnPropertyDescriptor()` method takes two arguments: the object and the property of the object, and returns the descriptor object.

The following example gets the descriptor object of the name property of the `product` object in the prior example.
```js
| 123456 | var descriptor = Object.getOwnPropertyDescriptor(product, 'name'); console.log(descriptor.configurable); // falseconsole.log(descriptor.writable); // falseconsole.log(descriptor.enumerable); // falseconsole.log(descriptor.value); // iPhone |
| ------ | ------------------------------------------------------------ |
|        |                                                              |
```
In this tutorial, you have learned about the JavaScript objects and various attributes of the properties of objects.

## JavaScript Prototype

### JavaScript Prototype Explained By Examples

**Summary**: JavaScript prototype is one of the most important concepts that every JavaScript developer must understand. This tutorial explains the prototype concept in detail and clears all confusions that you may have regarding prototype.

To follow this tutorial, you must [understand JavaScript objects](http://www.javascripttutorial.net/javascript-objects/). If you are not familiar with objects in JavaScript, you should follow the [understanding JavaScript objects](http://www.javascripttutorial.net/javascript-objects/) tutorial before going forward with this tutorial.

### Introduction to JavaScript prototype

By default, JavaScript engine provides the `Object()` function and an anonymous object that can be referenced to via the `Object.prototype.`

| 12   | console.log(Object);console.log(Object.prototype); |
| ---- | -------------------------------------------------- |
|      |                                                    |

The `Object.prototype` object has many built-in properties such as `toString(),` `valueOf(),` etc. It also has a property named `constructor` that points back to the `Object()` function.

| 1    | console.log(Object.prototype.constructor === Object); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Suppose circle represents a function and square represents an object. The following figure illustrates the relationships between the `Object()` function and the `Object.prototype` object:

![javascript-prototype](http://www.javascripttutorial.net/wp-content/uploads/2016/09/JavaScript-Prototype-300x109.png)

First, let’s define a function named `Foo` as follows:

| 123  | function Foo(name) {    this.name = name;} |
| ---- | ------------------------------------------ |
|      |                                            |

The `Foo()` function accepts an argument, adds the `name` property to the object, and sets the value of the `name` property to the argument.

Behind the scenes, JavaScript engine creates a new function `Foo()` and an anonymous object. The `Foo()` function has a property named `prototype` that points to the anonymous object. And the anonymous object has the `constructor` property points back to the `Foo()` function.

In addition, the `Foo.prototype` object is linked to the `Object.prototype` object via `[[Prototype]]`, which is known as *prototype linkage*. The prototype linkage is denoted by `[[Prototype]]` in the figure below.

![JavaScript Prototype - Function defined ](http://www.javascripttutorial.net/wp-content/uploads/2016/09/JavaScript-Prototype-Function-defined.png)

Second, add a new method named `whoAmI()` to the `Foo.prototype` object.

| 123  | Foo.prototype.whoAmI = function() {    return "I am " + this.name;} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

![JavaScript Prototype - add method to prototype](http://www.javascripttutorial.net/wp-content/uploads/2016/09/JavaScript-Prototype-Function.png)

Third, create a new instance of the `Foo` object.

| 1    | var a = new Foo('a'); |
| ---- | --------------------- |
|      |                       |

Internally, JavaScript engine creates a new object named `a` and links the `a` object to the `Foo.prototype` object via prototype linkage.

![JavaScript Prototype - create a new object](http://www.javascripttutorial.net/wp-content/uploads/2016/09/JavaScript-Prototype-New-Object.png)

The link of `a`, `Foo.prototype`, and `Object.protoype` is called *prototype chain*.

Fourth, create another instance of the `Foo` object named `b`.

| 1    | var b = new Foo('b'); |
| ---- | --------------------- |
|      |                       |

![JavaScript Prototype - create a new object](http://www.javascripttutorial.net/wp-content/uploads/2016/09/JavaScript-Prototype-second-object.png)

Fifth, add new `say()` method to the b object.

| 123  | b.say = function() {    console.log('Hi from ' + this.whoAmI());} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

JavaScript engine adds the `say()` method to the `b` object, not the `Foo.prototype` object.

![JavaScript Prototype - add method to object](http://www.javascripttutorial.net/wp-content/uploads/2016/09/JavaScript-Prototype-add-method-to-object.png)

Now, see the following code.

| 1    | console.log(a.constructor); // Foo |
| ---- | ---------------------------------- |
|      |                                    |

The object `a` does not have the `constructor` property, therefore, JavaScript engine goes up to the prototype chain to find it. Because the object `a` links to the `Foo.prototype` object via the prototype linkage and `Foo.prototype` has `constructor` property, JavaScript engine returns `Foo`. As the result, the following statement returns `true`.

| 1    | console.log(a.constructor === Foo); // true |
| ---- | ------------------------------------------- |
|      |                                             |

### Getting prototype linkage

The `__proto__` is pronounced as *dunder proto*. The `__proto__` is an [accessor property](http://www.javascripttutorial.net/javascript-objects/#accessor_property) of the `Object.prototype` object. It exposes the internal prototype linkage ( `[[Prototype]])` of an object through which it is accessed.

The `__proto__ `has been standardized in [ES6](http://www.javascripttutorial.net/es6/) to ensure the compatibility for web browsers. However, it may be depreciated in favor of `Object.getPrototypeOf()` in the future. Therefore, you should never use `__proto__` in your production code.

As you see in the previous diagram, the  `a.__proto__` exposes the `[[Prototype]]` that points to the `Foo.prototype` object. Similarly, `b.__proto__` also points to the same object as `a.__proto__:`

| 12   | console.log(a.__proto__ === Foo.prototype); // trueconsole.log(a.__proto__ === b.__proto__); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

As mentioned earlier, you should use the `Object.getPrototypeOf()` method instead of the `__proto__`. The `Object.getPrototypeOf()` method returns the prototype of a specified object.

| 1    | console.log(a.__proto__ === Object.getPrototypeOf(a)); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Another way that developers often used to get the prototype linkage when the `Object.getPrototypeOf()` method was not available is via the `constructor` property as follows:

| 1    | a.constructor.prototype |
| ---- | ----------------------- |
|      |                         |

The `a.constructor` returns `Foo`, therefore, `a.constructor.prototype` returns the prototype object.

### Shadowing

See the following method call.

| 1    | console.log(a.whoAmI()); // I am a |
| ---- | ---------------------------------- |
|      |                                    |

The `a` object does not have the method `whoAmI()` therefore when this method is called from the `a`object, JavaScript engine goes up to the prototype chain and finds it. In this case, it found the method in the `Foo.prototype` object and executed it.

Let’s add a new method to the object `a` with the same name of method in the `Foo.prototype` object.

| 123  | a.whoAmI = function() {    console.log('This is ' + this.name);} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

And call the `whoAmI()` method:

| 1    | console.log(a.whoAmI()); // This is a |
| ---- | ------------------------------------- |
|      |                                       |

Because we have the `whoAmI()` method in the `a` object, JavaScript engine just executes it immediately without looking it up in the prototype chain.

This is an example of shadowing. The `whoAmI()` method of the `a` object shadows the `whoAmI()`method of the prototype object to which the `a` object links.

Now you should understand all important concepts related to JavaScript prototype including prototype chain, prototype linkage, dunder proto, and shadowing.

## JavaScript Object Creation Patterns

### The Most Common Patterns To Create Objects In JavaScript

**Summary**: in this tutorial, you will learn various patterns to create objects in JavaScript and understand the pros and cons of each.

In the previous tutorial, you have learned how to create [JavaScript objects](http://www.javascripttutorial.net/javascript-objects/) using the object literal syntax. The object literal syntax is convenient for creating a single object. In case you want to create multiple similar objects, you need to use one of the following patterns.

- [Factory pattern](http://www.javascripttutorial.net/create-objects-in-javascript/#factory_pattern)
- [Constructor pattern](http://www.javascripttutorial.net/create-objects-in-javascript/#constructor_pattern)
- [Prototype pattern](http://www.javascripttutorial.net/create-objects-in-javascript/#prototype_pattern)
- [Constructor / prototype pattern](http://www.javascripttutorial.net/create-objects-in-javascript/#constructor_prototype_pattern)
- [Parasitic constructor pattern](http://www.javascripttutorial.net/create-objects-in-javascript/#parasitic_constructor_pattern)
- [Durable constructor pattern](http://www.javascripttutorial.net/create-objects-in-javascript/#durable_constructor_pattern)

### Factory pattern

The factory pattern uses a [function](http://www.javascripttutorial.net/javascript-function/) to abstract away the process of creating specific [objects](http://www.javascripttutorial.net/javascript-objects/). For example, the following `createAnimal()` function encapsulates the logic of creating the `animal` object.

| 123456789 | // factory patternfunction createAnimal(name) {    var o = new Object();    o.name = name;    o.identify = function() {        console.log("I'm " + o.name);    }    return o;} |
| --------- | ------------------------------------------------------------ |
|           |                                                              |

The `createAnimal()` function accepts an argument that will be used to initialize the `name` property of the `animal` object. To create a new object, you just need to call this function and pass in the `name`argument as follows:

| 12345 | var tom = createAnimal('Tom');var jerry = createAnimal('Jerry'); tom.identify(); // I'm Tomjerry.identify(); // I'm Jerry |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

Although the factory pattern can create multiple similar objects, it doesn’t allow you to identify what type of object it creates.

### Constructor pattern

JavaScript allows you to create a custom constructor function that defines the properties and methods of user-defined objects. By convention, the name of a constructor function in JavaScript starts with an uppercase letter. For example, the following rewritten the `animal` object of the prior example:

| 123456 | function Animal(name) {    this.name = name;    this.identify = function() {        console.log("I'm " + this.name);    };} |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

Unlike the factory pattern, the properties and methods of the `animal` object are assigned directly to the `this` object inside the constructor function.

At this point, JavaScript engine creates the `Animal()` function and an anonymous object. The `Animal()`function has the `prototype` property pointing to the anonymous object and the anonymous object has the `constructor` property pointing back to the `Animal()` function. In addition, JavaScript engine links the anonymous object to the global object.

![JavaScript Constructor Pattern](http://www.javascripttutorial.net/wp-content/uploads/2016/09/JavaScript-Constructor-Pattern.png)

 

To create a new instance of `Animal`, you use the `new` operator. For example:

| 1    | var donald = new Animal('Donald'); |
| ---- | ---------------------------------- |
|      |                                    |

Behind the scenes, JavaScript executes four steps:

1. Create a new object.
2. Set the `this` value of the constructor to the `new` object.
3. Execute code inside the constructor i.e., adding properties to the new object.
4. Return the new object.

The following figure illustrates the relationship between the  `donald` object and other objects.

 

![Create Objects in JavaScript - Constructor Pattern](http://www.javascripttutorial.net/wp-content/uploads/2016/09/Create-Objects-in-JavaScript-Constructor-Pattern.png)

See the following example.

| 1    | console.log(donald.constructor === Animal); // true |
| ---- | --------------------------------------------------- |
|      |                                                     |

In this example, because the  `donald` object does not have the `constructor` property, JavaScript engine follows the prototype chain to find it in the `Animal.prototype` object. It found the `constructor`property in the `Animal.prototype` object and in this case the `constructor` property points to the `Animal()` function, therefore the statement above returns `true`.

The  `donald` object is also an instance of `Animal` and `Object` as illustrated below.

| 12   | console.log(donald instanceof Animal); // trueconsole.log(donald instanceof Object); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

The disadvantage of the constructor pattern is that the same method `identify()` is duplicated in each instance. The following code creates a new Animal object named bob.

| 1    | var bob = new Animal('Bob'); |
| ---- | ---------------------------- |
|      |                              |

![Create Objects in JavaScript - Multiple Instances in Constructor Pattern](http://www.javascripttutorial.net/wp-content/uploads/2016/09/Create-Objects-in-JavaScript-Multiple-Instances.png)

As you see, the `identify()` method is duplicated in both  `donald` and `bob` objects. To solve this issue, you use the prototype pattern.

### Prototype pattern

The prototype pattern adds the properties of the object to the prototype object. Then, these properties are available and shared among all instances.

The following example uses the prototype pattern to rewrite the Animal object above.

| 12345678 | function Animal() {    // properties are added to prototype} Animal.prototype.name = 'Noname';Animal.prototype.identify = function() {    console.log("I'm " + this.name);} |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

![Create Objects in JavaScript - Prototype Pattern](http://www.javascripttutorial.net/wp-content/uploads/2016/09/Create-Objects-in-JavaScript-Prototype-Pattern.png)
Let’s create a new instance of the Animal.

| 123  | var donald = new Animal();donald.name = 'Donald'; // shadow the name propertydonald.identify(); // I'm Donald |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

![Create Objects in JavaScript - Prototype Pattern - New Instance](http://www.javascripttutorial.net/wp-content/uploads/2016/09/Create-Objects-in-JavaScript-Prototype-Pattern-new-Object.png)

In the line:

| 1    | donald.name = 'Donald'; // shadow the name property |
| ---- | --------------------------------------------------- |
|      |                                                     |

JavaScript engine adds the name property to the  `donald` object. As the result, both  `donald` and Animal.prototype objects has the same name property.

Inside the `identify()` method, the `this` object is set to the  `donald` object, therefore this.name references to the name property of the  `donald` object. As the result, the output of the following line:

| 1    | donald.identify(); |
| ---- | ------------------ |
|      |                    |

is the  string `I'm Donald`

Let’s remove the name property of the  `donald` object.

| 1    | delete donald.name; |
| ---- | ------------------- |
|      |                     |

and call the `identify()` method again.

| 1    | donald.identify(); //I'm Noname |
| ---- | ------------------------------- |
|      |                                 |

Now, JavaScript could not find the name property in the `donald` object, it follows the prototype chain and finds it in the `Animal.prototype` object. Hence, the `this.name` returns `Noname`.

For more information on the prototype, check it out the [JavaScript prototype tutorial](http://www.javascripttutorial.net/javascript-prototype/).

### Constructor / Prototype pattern

The combination of the constructor and prototype patterns is the most common way to define custom types. The constructor pattern defines object properties, while the prototype pattern defines methods and shared properties.

By using this pattern, all objects of the custom type share the method and each of them has its own properties. This constructor / prototype takes the best parts of both constructor and prototype patterns.

| 12345678910111213 | function Animal(name) {    this.name = name;} Animal.prototype.identify = function() {    console.log("I'm " + this.name);} var donald = new Animal('Donald');donald.identify(); // I'm Donald var bob = new Animal('Bob')bob.identify(); // I'm Bob |
| ----------------- | ------------------------------------------------------------ |
|                   |                                                              |

The following figure illustrates the relationships between objects in the constructor / prototype pattern.
![Create Objects in JavaScript - Prototype Pattern - Multiple Instances](http://www.javascripttutorial.net/wp-content/uploads/2016/09/Create-Objects-in-JavaScript-Constructor-Prototype-Pattern.png)

### Parasitic constructor pattern

In parasitic constructor pattern, you create a constructor function that creates an object and returns that object.

| 12345678 | function Animal(name) {    var o = new Object();    o.name = name;    o.identify = function() {        console.log("I'm " + o.name);    }    return o;} |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

In this example, the Animal constructor function is the same as the one in the factory pattern. However, you call it as a constructor using the `new` operator.

| 1    | var dog = new Animal('Bingo'); |
| ---- | ------------------------------ |
|      |                                |

By default, the `new` operator returns the object returned by the `constructor` function. If the `constructor` function does not return an object, the `new` operator creates that object instead.

### Durable constructor pattern

A durable object is an object that does not have public property and its methods don’t reference to the `this` object. The durable objects are often used in secure environments where accessing `this` and `new` are not allowed.

See the following example.

| 12345678910 | function secureAnimal(name) {    var o = new Object();    o.identify = function() {        console.log(name); //  no this    }    return o;} var alien = secureAnimal('?#@');alien.identify(); // ?#@ |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

The `alien` is a durable object that does not allow the external code to access its members without calling its methods.

In this tutorial, you have learned various patterns to create objects in JavaScript. Each pattern has pros and cons, choosing the appropriate one depends on your programming context.

## JavaScript Prototypal Inheritance

### The Utimate Guide To JavaScript Prototypal Inheritance

**Summary**: this tutorial teaches you JavaScript prototypal inheritance that helps you link object to another object for reusing functionality.

In other object-oriented programming languages such as C++, Java, C#, you define classes and create objects from the classes. A class is a blueprint of objects. In case you want to reuse the functionality of another class, you just need to extend it. This is called **class**ical inheritance.

JavaScript uses prototypal inheritance i.e., an [object](http://www.javascripttutorial.net/javascript-objects/) can inherit properties from another object. The prototypal inheritance is achieved via the prototype linkage.

### Inheritance and dunder proto (__proto__)

Suppose you have an object named `animal` that has a method called `walk().`

| 12345 | var animal = {    walk: function() {        console.log('walking');    }} |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

And another object named `bird` that has a method named `fly()`.

| 12345 | var bird = {    fly: function() {        console.log('flying');    }} |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

Suppose you want the `bird` object to inherit all properties from the `animal` object. In this case, you use the dunder proto ( `__proto__`) property as follows:

| 1    | bird.__proto__ = animal; |
| ---- | ------------------------ |
|      |                          |

When you access a property of the `bird` object that does not exist, JavaScript engines follows the prototype chain and finds the property in the `animal` object as shown in the following example.

| 1    | bird.walk(); // walking |
| ---- | ----------------------- |
|      |                         |

In this example, the `walk()` method does not exist in the `bird` object, therefore, JavaScript engine follows the prototype chain and finds it in the `animal` object.

If JavaScript engine found a property in the `bird` object, it would not follow the `__proto__` link as in this example.

| 1    | bird.fly(); // flying |
| ---- | --------------------- |
|      |                       |

Let’s add a new property to both `animal` and `bird` objects, and change the `walk()` method of the `animal` object.

| 123456789101112131415 | var animal = {    legs: 4,    walk: function() {        console.log('walking on ' + this.legs + ' legs');    }} var bird = {    legs: 2,    fly: function() {        console.log('flying');    }} bird.__proto__ = animal; |
| --------------------- | ------------------------------------------------------------ |
|                       |                                                              |

When you call the `walk()` method on the `bird` object

| 1    | bird.walk(); |
| ---- | ------------ |
|      |              |

Internally, JavaScript engine executes it in two steps.

1. First, it finds the `walk()` method in the `bird` object. Because there’s no `walk()` method there, it follows the prototype chain to look up the `walk()` method in the animal object.
2. Second, it executes the `walk()` method with the `this` set to the `bird` object, not `animal`object,  so the `this.legs` property stores the value defined in the `bird` object.

As the result, the `bird` object (child object) calls the method of the `animal` object (parent object), but the  `this` is set to `bird` object itself. By definition, the `bird` object inherits all properties from the `animal` object.

Unfortunately, the dunder proto ( `__proto__`) has not been standardized until ES6. However, ES6 added the `__proto__` to as a standard just for compatibility issue. Therefore, you should use `__proto__` for proof of concept only.

### JavaScript prototypal inheritance – the old way

Douglas Crockford had an article titled “[Prototypal Inheritance in JavaScript](http://javascript.crockford.com/prototypal.html)” in 2006. He introduced a function that allows an object to inherit from another object without defining a custom type.

| 12345 | function object(b) {    function F();    F.prototype = o;    return new F();} |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

Essentially, the `object()` function performs a shallow copy of any object you passed into it. According to Crockford, you have an object that you want to use as the base of another object. First, you should pass this object into the `object()` function and get the resulting object i.e., the derived object. Then, you modify the derived object accordingly.

See the following example.

| 123456789101112131415 | var animal = {    legs: 4,    walk: function() {        console.log('walking on ' + this.legs + ' legs');    }} var bird = object(animal);bird.legs = 2;bird.fly = function() {    console.log('flying');} bird.walk(); // walking on 2 legsbird.fly(); // flying |
| --------------------- | ------------------------------------------------------------ |
|                       |                                                              |

In this example, the `bird` object inherits properties from the `animal` object as in the previous example.

### A standard way to implement prototypal inheritance

ES5 provided a standard way to work with prototypal inheritance by adding the `Object.create()`method. The `Object.create()` method creates a new object based on specified prototype object. This method accepts two arguments. The first argument is an object to be used as the prototype for the new object. And the second argument, if provided, is an optional object that defines additional properties of the new object.

The `Object.create()` method accepts two arguments where a first argument is an object used as the prototype for the new object and the second argument if provided, is an optional object that defines additional properties of the new object.

Suppose, you have an `animal` object as follows:

| 123456 | var animal = {    legs: 4,    walk: function() {        console.log('walking on ' + this.legs + ' legs');    }} |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

The following creates an empty `bird` object with the  __proto__ of the `animal` object.

| 1    | var bird = Object.create(animal); |
| ---- | --------------------------------- |
|      |                                   |

After that, you can add properties to the `bird` object.

| 1234 | bird.legs = 2;bird.fly = function() {    console.log('flying');} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Or you can do all of these steps in one statement as follows:

| 123456 | var bird = Object.create(animal, {    legs: 2,    fly: function() {        console.log('flying');    }}); |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

ES5 introduced the `Object.getPrototypeOf()` method that returns the prototype of a specified object. For example:

| 1    | console.log(Object.getPrototypeOf(bird) === animal); |
| ---- | ---------------------------------------------------- |
|      |                                                      |

In this tutorial, you have learned how to implement JavaScript prototypal inheritance using the `Object.create()` method.

## JavaScript this Keyword

### Demystifying JavaScript this Keyword with Practical Examples

**Summary**: this tutorial helps you understand the JavaScript `this` keyword clearly through practical examples.

If you have been working with other programming languages such as C++, Java or PHP, you already familiar with the `this` keyword. In these languages, the `this `keyword represents an instance of the current object in the method of the class. And `this` keyword is only relevant within the method of the class, meaning that you cannot use it outside of a method.

JavaScript has the `this` keyword that behaves differently from other programming languages, which may confuse you at first. In JavaScript, you can use the `this` keyword in the global and [function](http://www.javascripttutorial.net/javascript-function/)contexts. Moreover, the behavior of the  `this` keyword changes between strict and non-strict mode.

### Global context

In the global context, `this `refers to the global object, which is the `window` in the web browser or `global` in node.js. This behavior is consistent whether the of the strict mode is applied or not.

See the following example:

| 1    | console.log(this === window); // true |
| ---- | ------------------------------------- |
|      |                                       |

If you assign a property to `this` object in the global context, JavaScript will add it to the global object as shown below:

| 123  | this.p = 10;console.log(window.p); // 10 |
| ---- | ---------------------------------------- |
|      |                                          |

### Function context

In JavaScript, you can invoke a [function](http://www.javascripttutorial.net/javascript-function/) in the following ways:

- [Function invocation](http://www.javascripttutorial.net/javascript-this/#function_invocation)
- [Method invocation](http://www.javascripttutorial.net/javascript-this/#method_invocation)
- [Constructor invocation](http://www.javascripttutorial.net/javascript-this/#constructor_invocation)
- [Indirect invocation](http://www.javascripttutorial.net/javascript-this/#indirect_invocation)

Each invocation defines its own context, therefore, `this` behaves differently than you may expect.

#### Simple function invocation

In the non-strict mode, `this` refers to the global object when the function is called as shown in the following example:

| 123456 | function add(a, b) {   console.log(this === window); // true   return a + b; } add(10,20); |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

When you call the `add()` function, JavaScript sets `this` as the global object, which is the `window` in the web browser.

In the strict mode, JavaScript set this to `undefined`. Consider the following example:

| 1234567 | function add(a, b){   "use strict"   console.log(this === undefined);   return a + b;} add(a,b); |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

To set the strict mode, you can use the directive `"use strict"` at the beginning of the file. In case, you want to apply the strict mode to a specific function, you place it at the top of the function body. Note that strict mode was available since ECMAScript 5.1

Notice that the strict mode also applies to not only function but also the inner functions within the function. Here is an example:

| 123456789101112131415161718 | function add(a,b){  "use strict";  console.log(this === undefined);    function logResult(msg){    console.log(this === undefined);    console.log(msg);  }   var result = a + b;  logResult(result);  return result;} add(10,20);// true// true// 30 |
| --------------------------- | ------------------------------------------------------------ |
|                             |                                                              |

Inside the `logResult()` inner function, JavaScript sets `this` to `undefined` as shown in the log.

A common mistake you may have is to think that `this` is the same in an inner function as in the outer function. The truth is that the context of the inner function depends on how it is invoked not the context of the outer function. Consider the following example.

| 1234567891011 | var product = {  netPrice: 100,  tax: 0.08,  getPrice: function(){      function calculateTax(){        return this.netPrice * this.tax;      }      return this.netPrice + calculateTax();  }}   console.log(product.getPrice()); // NaN |
| ------------- | ------------------------------------------------------------ |
|               |                                                              |

The result is `NaN` which is not what you expected.

The this in the `calculateTax()` function is set to the global object. However, the global object does not have netPrice and tax properties, therefore, the `calculateTax()` function returns `undefined`. As the result the `getNetPrice()` returns `undefined`.

To fix the issue, you use the `call()` method of the Function object.

| 1    | function_name.call(this); |
| ---- | ------------------------- |
|      |                           |

The `call()` method uses the first parameter as this inside the function object. Therefore, you can use it to set the intended context for the function. See the following modification of the code above:

| 1234567891011121314 | "use strict"; var product = {  netPrice: 100,  tax: 0.08,  getPrice: function(){      function calculateTax(){        return this.netPrice * this.tax;      }      return this.netPrice + calculateTax.call(this);  }} console.log(product.getPrice()); // 108 |
| ------------------- | ------------------------------------------------------------ |
|                     |                                                              |

#### Method invocation

When you call a method of an object, JavaScript sets `this` to the object that owns the method. See the following `car` object.

| 12345678 | var car = {  brand: 'Honda',  getBrand: function(){    return this.brand;  }  } console.log(car.getBrand()); // Honda |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

In this example, this inside the `getBrand()` method refers to the `car` object.

Because a method is a property of an object which is a value, you can save it into a variable.

| 1    | var hondaCar = car.getBrand; |
| ---- | ---------------------------- |
|      |                              |

And then call the method via the variable:

| 1    | console.log(hondaCar()); // undefined |
| ---- | ------------------------------------- |
|      |                                       |

You got `undefined` instead of `"Honda"` because when you call a method without specifying its object, JavaScript sets `this` to the global object in strict mode and `undefined` in the non-strict mode.

To fix this issue, you use the `bind()` method of the `Function.prototype` object. The `bind()` method creates a new function with the `this` keyword is set to a specified value.

| 12   | var hondaCar = car.getBrand.bind(car);console.log(hondaCar()); // Honda |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

In this example, when the `hondaCar()` is called, the `this` keyword is bound to the car object.

#### Constructor invocation

When you use the new keyword to create an instance of a function object, you use the function as a constructor.

The following example declares a `Car` function, then invokes it as a constructor.

| 12345678910 | function Car(brand){  this.brand = brand;} Car.prototype.getBrand = function(){  return this.brand;} var car = new Car('Honda');console.log(car.getBrand()); |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

The expression `new Car('Honda')` is a constructor invocation of the `Car` function. JavaScript creates a new object and sets `this` keyword to this newly created object.

This pattern works great with only one potential problem. Now, you can invoke the `Car()` as a function or as a constructor. If you omit the `new` keyword as follows:

| 123  | var bmw = Car('BMW');console.log(bmw.brand);// => TypeError: Cannot read property 'brand' of undefined |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Because this in the `Car()` function is set to the global object, the `bmw.brand` returns `undefined`.

To make sure that the `Car()` function is always invoked using constructor invocation, you add a check at the beginning of the `Car()` function as follows:

| 123456 | function Car(brand){  if(!(this instanceof Car){    throw Error('Must use the new operator to call the function');  }  this.brand = brand;} |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

ES6 introduced a metaproperty named [`new.target`](http://www.javascripttutorial.net/es6/javascript-new-target/) that allows you to detect whether a function is invoked as a simple invocation or as a constructor.

You can modify the `Car()` function that uses the `new.target` metaproperty as follows:

| 123456 | function Car(brand){  if(!new.target){    throw Error('Must use the new operator to call the function');  }  this.brand = brand;} |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

#### Indirect Invocation

In JavaScript, functions are the first-class citizen. In other words, functions are objects, which are instances of the [Function type](http://www.javascripttutorial.net/javascript-function-type/).

The Function type has two methods: `call()` and `apply()` that allow you to pass the context as the first argument to these functions. See the following example.

| 123456789 | function getBrand(prefix){  console.log(prefix + this.brand);} var honda = {brand: 'Honda'};var audi = {brand: 'Audi'}; getBrand.call(honda,"It's a "); // "It's a Honda"getBrand.call(audi,"It's an ");// "It's a Audi" |
| --------- | ------------------------------------------------------------ |
|           |                                                              |

In this example, we called the `getBrand()` function indirectly using the `call()` method.

We passed `honda` and  `audi` object as the first argument of the `call()` method, therefore, in each call we get the corresponding brand.

The `apply()` method is similar to the `call()` method except that its second argument is an array of arguments.

| 12   | getBrand.apply(honda,["It's a "]); // "It's a Honda"getBrand.apply(audi,["It's an "]);// "It's a Audi" |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

### Arrow functions

[ES6 ](http://www.javascripttutorial.net/es6/)introduced a new concept named [arrow function](http://www.javascripttutorial.net/es6/javascript-arrow-function/). In arrow functions, JavaScript sets this lexically. It means that the arrow function does not create its own execution context, but inherits this from the outer function where the arrow function is defined.

See the following example:

| 12   | let getThis = () => this;console.log(getThis() === window); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

In this example, this is set to the global object i.e.,`window` in the web browser.

Because the arrow function does not create its own execution context, defining a method using an arrow function causes an issue as shown in the following example.

| 12345678910 | function Car(){  this.speed = 120;} Car.prototype.getSpeed = () => {  return this.speed;} var car = new Car();car.getSpeed(); // TypeError |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

Inside the `getSpeed()` method, this refers to the global object, not the `Car` object. Therefore, `car.getSpeed()` invocation cause error because the global object does not have speed property.

In this tutorial, you have learned how JavaScript `this` behaves in different contexts.
