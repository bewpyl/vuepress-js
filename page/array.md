---
sidebar: auto
---

# JavaScript Array

## JavaScript Array

**Summary**: in this tutorial, you will learn about JavaScript array type and some of its unique characteristics.

### Introduction to JavaScript array

In JavaScript, an array is an ordered list of data. An array has the following special characteristics in comparison with the array of other programming languages such as Java, C/C++, etc.

1. First, an array can hold data of the different [types](http://www.javascripttutorial.net/javascript-data-types/) in each slot i.e., an array can hold elements with mixed of [numbers](http://www.javascripttutorial.net/javascript-data-types/#number), [strings](http://www.javascripttutorial.net/javascript-data-types/#string), [objects](http://www.javascripttutorial.net/javascript-data-types/#object), etc.
2. Second, the length of an array is dynamically sized and auto-growing.

### Creating JavaScript arrays

JavaScript provides you with two ways to create an array. The first one is to use the `Array` constructor as follows:
```js
1  var scores = new Array(); 
```
The `scores` array is empty i.e. it holds no element.

If you know the number of elements that the array will hold, you can create an array with an initial size as in the following example:
```js
1  var scores = Array(10);
```

To create an array with initial elements, you pass the elements as a comma-separated list in the `Array()` constructor. The following example creates the `scores` array that holds five numbers:
```js
1  var scores = new Array(9,10,8,7,6);
```

It’s important to notice that if you use the array constructor to create an array and pass in a number, you are creating an array with an initial size. However, if you pass in one argument of another type, you create an array that holds that element.

See the following examples:
```js
1  var athletes = new Array(3); // creates an array with initial size 3
2  var scores = new Array(1, 2, 3); // create an array with three numbers 1,2 3
3  var signs = new Array('Red'); // creates an array with one element ('Red')
```

JavaScript allows you to omit the `new` operator when you use the array constructor. For example, the following statement creates the `artists` array. 
```js
1  var artists = Array();
```

The second way, maybe the more preferred way, to create an array is by using the array literal notation as follows:
```js
1  var array_name = [element1, element2, element3];
```

The array literal form uses the square brackets [] to wrap a comma-separated list of elements. For example, the following statement creates `colors` array of three colors:
```
1  var colors = ['red', 'green', 'blue'];
```

It’s possible to create an empty array by using empty square brackets.
```js
1  var emptyArray = [];
```

The following example creates an array of two [undefined](http://www.javascripttutorial.net/javascript-data-types/#undefined) elements.
```js
1  var nonEmptyArry = [,,];
2  console.log(nonEmptyArray); // [undefined, undefined]
```
### Accessing JavaScript array elements

You can access elements of an array by using the square brackets `[]`. The first element of the array start with 0, the second element starts with 1, and so on.

For example, the following example creates an array of three strings.

```js
1  var mountains = ['Everest', 'Fuji', 'Nanga Parbat'];
```

The following statements show how to access the elements of the `mountains` array.
```js
1  console.log(mountains[0]); // 'Everest'
2  console.log(mountains[1]); // 'Fuji'
3  console.log(mountains[2]); // 'Nanga Parbat'
```


To change the value of an element in the array, you use assign that element a value as follows:
```js
1  mountains[2] = 'K2';
```

### The size of an array

The array uses the `length` property to store the current number of elements it holds. You can access get the value of the `length` property as shown in the following example.
```js
1  console.log(mountains.length); // 3
```

The `length` property is writable therefore you can [insert or delete elements](http://www.javascripttutorial.net/javascript-array-splice/) by changing the value of the `length` property.

If you set the `length` property to a value that is greater than the number of elements in the array, the new elements will be added with the initial values of [`undefined`](http://www.javascripttutorial.net/javascript-data-types/#undefined).

For example, we change the `length` property of the `mountains` array to 4 to append one element with an initial value of `undefined` at the end of the array.
```js
1  // append 1 element
2  mountains.length = 4;
3  console.log(mountains[3]); // undefined
```

Similarly, the following example sets the `length` property of the `mountains` array to 2 to remove the last two elements of the array. When we access the third element of the array, it returns `undefined`.
```js
1  // remove the last 2 elements
2  mountains.length = 2;
3  console.log(mountains[2]); // undefined
```

Note that the maximum number of elements that the JavaScript array can hold is 4,294,967,295 which is sufficient enough for a typical application.

### Basic operations on arrays

All arrays are instances of the `Array` type. Therefore, the `typeof` of an array [variable ](http://www.javascripttutorial.net/javascript-variables/)returns `object`as shown in the following example:

```js
1  var seas = ['Black Sea', 'Caribbean Sea', 'North Sea', 'Baltic Sea'];
2  console.log(typeof seas); // object
```

To check if a variable is an array, you use `Array.isArray()` method as follows:
```js
1  console.log(Array.isArray(seas)); // true
```
When you call the `toString()` and `valueOf()` methods of an array, you get a string represented as a comma-separated list of elements as shown in the following example:
```js
1  console.log(seas.toString());
2  // Black Sea,Caribbean Sea,North Sea,Baltic Seaconsole.log(seas.valueOf());
```
If you want to have a string representation of an array differently, you can use the `join()` method.

The following example uses the `join()` method to returns a string representation of the `mountains`array. However, the elements are separated by the pipe (|) character instead.
```js
1  console.log(seas.join('\|')); 
2  // Black Sea\|Caribbean Sea\|North Sea\|Baltic Sea  
```
If an element of the array is [`null`](http://www.javascripttutorial.net/javascript-data-types/#null) or `undefined`, the `toString(),` `valueOf()`, and `join()` will treats it as an empty string in the resulting string. Here is an example.
```js
1  var mixedValues = [1, 2, null, 'A', undefined, 3];
2  console.log(mixedValues.toString());  // 1,2,,A,,3
```

Now you should have a basic understanding of JavaScript array and some of its unique characteristics. In the next tutorial, you will learn how to manipulate array elements such [inserting](http://www.javascripttutorial.net/javascript-array-splice/), [deleting](http://www.javascripttutorial.net/javascript-array-splice/), [replacing](http://www.javascripttutorial.net/javascript-array-splice/), [sorting](http://www.javascripttutorial.net/javascript-array-sort/), [filtering](http://www.javascripttutorial.net/javascript-array-filter/), [reducing](http://www.javascripttutorial.net/javascript-array-reduce/), etc.

## Javascript Stack: push() & pop()
### Implementing Javascript Stack Using an Array

**Summary**: this tutorial introduces you to the JavaScript stack data structure and shows you how to use an array as a stack.

### Introduction to the stack data structure

A stack is a data structure that holds a list of elements. A stack works based on the LIFO principle i.e., Last In, First out, meaning that the most recently added element is the first one to remove.

A stack has two main operations that occur only at the top of the stack: push and pop. The push operation places an element at the top of stack whereas the pop operation removes an element from the top of the stack.

The name *stack* comes from the analogy to a set of physical items e.g., DVD disc, books, stacked on top each other.![JavaScript Stack: A Stack of books analogy](http://www.javascripttutorial.net/wp-content/uploads/2016/08/stack-of-books.jpg)

A stack has many applications. For example, the simplest one is to reverse a word. To do it, you push a word into the stack, letter by letter, and pop the letters from the stack.

The other applications of the stack are “undo” mechanism in text editors, syntax parsing, [function](http://www.javascripttutorial.net/javascript-function/) call, and expression conversion (infix to postfix, infix to prefix, postfix to infix, and prefix to infix).

JavaScript [Array](http://www.javascripttutorial.net/javascript-array/) type provides the `push()` and `pop()` methods that allow you to use an array as a stack.

### push() method

The `push()` method allows you to add one or more elements to the end of the array. The `push()`method returns the value of the `length` property that specifies the number of elements in the array.

If you consider an array as a stack, the `push()` method adds one or more element at the top of the stack. The following example creates an empty array named `stack` and adds five numbers, one by one, at the end of the `stack` array. It is like to push each number into the top of the stack.
```js
 1  var stack = [];
 2
 3  stack.push(1);
 4  console.log(stack); // [1]
 5
 6  stack.push(2);
 7  console.log(stack); // [1,2]
 8
 9  stack.push(3);
10  console.log(stack); // [1,2,3]
11
12  stack.push(4);
13  console.log(stack); // [1,2,3,4]
14
15  stack.push(5);
16  console.log(stack); // [1,2,3,4,5] 
                                                          
```

The following figure illustrates each step in the script above.

![JavaScript Stack Push Operations](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Stack-Push-Operations.png)

Initially, the stack is empty. Each time, we call the `push()` method to add a number to the stack. After 5 calls, the stack has 5 elements.

Note that the `push()` method also allows you to add multiple items to the end of the array at a time.

### pop() method

The `pop()` method removes the element at the end of the array and returns the element to the caller. If the array is empty, the `pop()` method returns [undefined](http://www.javascripttutorial.net/javascript-data-types/#undefined).

The following example shows how to pop elements from the top of the stack using the `pop()` method.
```js
 1  console.log(stack.pop()); //  5
 2  console.log(stack); // [1,2,3,4];
 3
 4  console.log(stack.pop()); //  4
 5  console.log(stack); // [1,2,3];
 6
 7  console.log(stack.pop()); //  3
 8  console.log(stack); // [1,2];
 9
10  console.log(stack.pop()); //  2
11  console.log(stack); // [1];
12
13  console.log(stack.pop()); //  1
14  console.log(stack); // []; -> empty
15
16  console.log(stack.pop()); //  undefined 
```

The figure below illustrates each step in the script.

![JavaScrippt Stack Pop](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScrippt-Stack-Pop.png)

Initially, the stack has 5 elements. The `pop()` method removes the element at the end of the array i.e., at the top of the stack one at a time. After five operations, the stack is empty.

### Reverse a string using a JavaScript stack

The following example shows you how to reverse a string using a stack.
```js
 1  function reverse(str) {  
 2      var stack = []; 
 3      // push letter into stack
 4      for (var i = 0; i < str.length; i++) {
 5          stack.push(str[i]);
 6      }
 7      // pop letter from the stack
 8      var reverseStr = '';
 9      while (stack.length > 0) {
10          reverseStr += stack.pop();
11      }
12}
13  console.log('JavaScript Stack'); //kcatS tpircSavaJ |
```

How the script works.

The `reverse()` function accepts a string argument and returns its reversed version with the following logic:

1. First, loop through the `str` and push each letter into the `stack` array.
2. Second, pop each letter from the stack and construct the reversed string.

In this tutorial, we have shown you how to use an array as a JavaScript stack data structure that has two main operations: push and pop.

## JavaScript Queue: push() & shift()

**Summary**: in this tutorial, we will introduce you the queue data structure and show you how to implement a JavaScript queue using methods of the Array.

### Introduction to the queue data structure

A queue is an ordered list of elements where an element is inserted at the end of the queue and is removed from the front of the queue. Unlike a [stack](http://www.javascripttutorial.net/javascript-stack/) , which works based on the last-in, first-out (LIFO) principle, a queue works based on the first-in, first-out (FIFO) principle.

A queue has two main operations involving inserting a new element and removing an existing element. The insertion operation is called *enqueue*, and the removal operation is called *dequeue*. The enqueue operation inserts an element at the end of the queue, whereas the dequeue operation removes an element from the front of a queue.

The following figure illustrates a queue:

![JavaScript Queue Illustration](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Queue-Illustration.png)

Another important operation of a queue is getting the element at the front called *peek*. Different from the *dequeue* operation, the *peek* operation just returns the element at the front without modifying the queue.

The name *queue* comes from the analogy to a queue of customers at a bank. The customer who comes first will be served first, and the one who comes later is queued at the end of the queue, and of course will be served later.

### Implementing a JavaScript queue using an array

You can use an [array](http://www.javascripttutorial.net/javascript-array/) as a queue because the `Array` type provides two methods that are equivalent to the queue operations.

- Add an element at the end of the array using the `push()` method. This method is equivalent to the enqueue operation.
- Remove an element from the front of an array using the `shift()` method. It is the same as dequeue operation.

Let’s implement a JavaScript queue data structure by using an array.

The following is the constructor function of the queue:
```js
1  function Queue() { 
2      this.elements = [];
3  }
```

The `Queue()` constructor function uses an array to store its elements.

The `enqueue()` method adds an element at the end of the queue. We use the `push()` method of the array object to insert the new element at the end of the queue.
```js
1  Queue.prototype.enqueue = function (e) {
2    this.elements.push(e);
3  };
```

The `dequeue()` method removes an element from the front of the queue. In the `dequeue()` method, we use the `shift()` method of the array to remove an element at the front of the queue.
```js
1  // remove an element from the front of the queue 
2  Queue.prototype.dequeue = function () {
3  return this.elements.shift();
4  }; 
```

The `isEmpty()` method checks if a queue is empty by checking if the `length` property of the array is zero.
```js
1  // check if the queue is empty
2  Queue.prototype.isEmpty = function () {
3       return this.elements.length == 0;
4  };
```

The `peek()` method accesses the element at the front of the queue without modifying it.
```js
1  // get the element at the front of the queue
2  Queue.prototype.peek = function () { 
3       return !this.isEmpty() ? this.elements[0] : undefined;
4  };
```

To create a new queue from the `Queue()` constructor function, you use the new keyword as follows:
```js
1  var q = new Queue();
```
To enqueue numbers from 1 to 7, you use the following code.
```js
1  for (var i = 1; i <= 7; i++) { 
2       q.enqueue(i);
3  }
```

To get the number at the front of the queue, you use the `peek()` method.
```js
1  // get the current item at the front of the queue
2  console.log(q.peek()); // 1 
```

To get the current length of the queue, you use the `length()` method as in the following example.

```js
1  // get the current length of queue
2  console.log(q.length()); // 7 
```

To remove the element at the front of the queue, you use the dequeue method as follows:
```js
1  // dequeue all elements
2  while (!q.isEmpty()) { 
3       console.log(q.dequeue());
4  }
5  //1
6  //2
7  //3
8  //4
9  //5
10 //6
11 //7
```

Now you should have a good understanding of the queue data structure and know how to use array’s methods to implement a JavaScript queue.

## Manipulating Elements: splice()

### JavaScript Array Splice: Delete, Insert, and Replace

**Summary**: this tutorial shows you how to use the JavaScript Array splice method to delete existing elements, insert new elements, and replace elements in an array.

JavaScript [Array](http://www.javascripttutorial.net/javascript-array/) type provides a very powerful `splice()` method that allows you to insert new elements into the middle of an array. However, you can use this method to delete and replace existing elements as well.

### Deleting elements using JavaScript array splice

To  delete elements in an array, you pass two arguments to the `splice()` method as follows:
```js
1  Array.splice(position,num);
```
The `position` argument specifies the position of the first item to delete and the `num` argument determines the number of element to delete.

The `splice()` method changes the original array and returns an array that contains the deleted elements.

Let’s take a look at the following example.

Suppose, we have an array `scores` that contains five numbers from 1 to 5.

```js
1  var scores = [1, 2, 3, 4, 5];
```

The following statement deletes three elements of the `scores` array starting from the first element.
```js
1  var deletedScores = scores.splice(0, 3);
```
The `scores` array now contains two elements.

```js
1  console.log(scores); //  [4, 5] 
```

And the `deletedScores` array contains three elements.
```js
1  console.log(deletedScores); // [1, 2, 3] 
```

The following figure illustrates the `scores.splice(0,3)` method call above.

![JavaScript Array Splice Delete Example](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Array-Splice-Delete-Example.png)

### Inserting elements using JavaScript array splice

You can insert one or more element into an array by passing three or more arguments to the `splice()`method with the second argument is zero.

Consider the following syntax.
```js
1  Array.splice(position,0,new_element_1,new_element_2,...); 
```

In this syntax:

- The `position` argument specifies the starting position in the array that the new elements will be inserted.
- The second argument is zero (0) that instructs the `splice()` method to not delete any elements.
- The third argument, fourth argument, and so on are the new elements that are inserted into the array.

Note that the `splice()` method actually changes the original array. Also, the `splice()` method does not remove any elements, in this case, therefore, it returns an empty array. See the following example.

Assuming that you have an array named `colors` with three strings.
```js
1  var colors = ['red', 'green', 'blue'];
```

The following statement inserts one element after the second element.
```js
1  colors.splice(2, 0, 'purple');
```

The `colors` array now has four elements with the new element inserted at the second position.
```js
1  console.log(colors); // ["red", "green", "purple", "blue"] 
```

The following figure demonstrates the method call above.

![JavaScript Array Splice Insert Example](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Array-Splice-Insert-Example.png)

You can insert more than one element by passing the fourth argument, fifth argument, and so on to the `splice()` method as in the following example.

```js
1  colors.splice(1, 0, 'yellow', 'pink');
2  console.log(colors);
3  // ["red", "yellow", "pink", "green", "purple", "blue"] 
```

### Replacing elements using JavaScript array splice

The `splice()` method allows you to insert new elements into an array while deleting existing elements simultaneously.

To do this, you pass at least three arguments with the second one specify the number of items to delete and the third one is the elements to insert.

Note that the number of elements to delete needs not to be the same as the number of elements to insert.

Suppose, you have an array of programming languages with four elements as follows.
```js
1  var languages = ['C', 'C++', 'Java', 'JavaScript'];
```

The following statement replaces the second element by a new one.
```js
1  languages.splice(1, 1, 'Python');
```

The `languages` array now still has four elements with the new second argument is `'Python'` instead of `'C++'`.
```js
1  console.log(languages);
2 // ["C", "Python", "Java", "JavaScript"] 
```                                                             

The following figure illustrates the method call above.

![JavaScript Array Splice Replace Example](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Array-Splice-Replace-Example.png)

You can replace one element by multiple elements by passing more arguments to the `splice()`method as follows:
```js
1  languages.splice(2,1,'C#','Swift','Go');
```

The statement deletes one element from the second element i.e., `Java` and inserts three new elements into the `languages` array. The result is as follows.
```js
1  console.log(languages); // ["C", "Python", "C#", "Swift", "Go", "JavaScript"]
```

In this tutorial, you have learned how to use the JavaScript Array splice method to delete existing elements, insert new elements, and replace elements in an array.

## Sorting Elements: sort()

### JavaScript Array sort: Sorting Array Elements

**Summary**: in this tutorial, you will learn how to use the JavaScript array sort method to sort arrays of numbers, string, and objects.

### Introduction to JavaScript array sort method

The `sort()` method allows you to sort elements of an [array](http://www.javascripttutorial.net/javascript-array/) in place. Besides returning the sorted array, the `sort()` method also sorted the array that you pass in.

By default, the `sort()` method uses string Unicode code points to determine the order of the elements.

The following illustrates the syntax of the `sort()` method.
```js
1  Array.sort([comparer])
```

The `sort()` method accepts an optional argument which is a [function](http://www.javascripttutorial.net/javascript-function/) that compares two elements of the array.

If you omit the compare function, the `sort()` method sorts the elements with the sort order based on the Unicode code point values of elements.

Note that the `sort()` method will convert the element to a string for sorting in case the type of the element is not the string.

The compare function of the `sort()` method accepts two arguments and returns a value that determines the sort order. See the following compare function syntax:
```js
1  function compare(a,b) {
2     // ...
3  } |
```

The `compare()` function accepts two arguments `a` and `b`. The `sort()` method will sort elements based on the return value of the `compare()` function with the following rules:

1. If `compare(a,b)` is less than zero, the `sort()` method sorts `a` to a lower index than `b`. In other words, `a` will come first.
2. If `compare(a,b)` is greater than zero, the `sort()` method sort `b` to a lower index than `a`, i.e., b will come first.
3. If `compare(a,b)` returns zero, the `sort()` method considers a equals b and leaves their positions unchanged.

### Sorting arrays of strings

Suppose you have an array of string named `animals` as follows:

```js
1  var animals = [    'cat', 'dog', 'elephant', 'bee', 'ant'];
```

To sort the elements of the `animals` array in ascending order alphabetically, you use the `sort()`method without passing the compare function as in the following example:

```js
1  animals.sort();
2  console.log(animals);
3  // ["ant", "bee", "cat", "dog", "elephant"]
```

To sort the `animals` array in descending order, you need to change the logic of the compare function and pass it to the `sort()` method as the following example.
```js
 1  // descending order
 2  animals.sort(function (a, b) {
 3  if (a > b) {  
 4    return -1;
 5  }
 6
 7  if (b > a) {
 8    return 1;
 9  }   
10  return 0;});
11  console.log(animals);
12  // ["elephant", "dog", "cat", "bee", "ant"] |
```

Suppose you have an array that contains elements in both uppercase and lowercase as follows:
```js
1  // sorting array with mixed casesvar mixedCase
2  Animals = [    'Cat', 'dog', 'Elephant', 'bee', 'ant'];
```

To sort this array alphabetically, you need to use a custom compare function to convert all elements to the same case e.g., uppercase for comparison and pass that function to the `sort()` method.
```js
 1  mixedCaseAnimals.sort(function (a, b) { 
 2  var x = a.toUpperCase(),        
 3  y = b.toUpperCase();
 4  if (x > y) {        
 5    return 1;
 6    }
 7  if (x < y) {
 8    return -1;    
 9  }    
10      return 0;});  
11  console.log(mixedCaseAnimals);
12  ["ant", "bee", "Cat", "dog", "Elephant"]
```

#### Sorting array of strings with non-ASCII characters

The `sort()` method is working fine with the strings with ASCII characters. However, for the strings with non-ASCII characters e.g., é, è, etc., the `sort()` method will not work correctly.

See the following example.
```js
1  var animaux = ['zèbre', 'abeille', 'écureuil', 'chat'];
2  animaux.<code>sort()</code>;
3  // ["abeille", "chat", "zèbre", "écureuil"]
``` 

As you see, the `écureuil` string should come before the `zèbre` string.

To resolve this, you use the `localeCompare()` method of the `String` object to compare strings in a specific locale. Here is the solution.
```js
1  animaux.sort(function (a, b) {
2     return a.localeCompare(b);});
3  console.log(animaux);
4  // ["abeille", "chat", "écureuil", "zèbre"]
```

As shown above, the elements of the `animaux` array are in correct order.

### Sorting an array of numbers

Suppose you have an array of numbers named `scores` as in the following example.
```js
1  var scores = [9, 80, 10, 20, 5, 70];
```
To sort an array of numbers numerically, you need to pass in a custom compare function that compares two numbers. The following example sorts the `scores` array numerically in ascending order.
```js
1  // sort numbers in ascending order
2  scores.sort(function (a, b) {
3    return a - b;});
4  console.log(scores); 
```
In ES6, you can use arrow function to make the code cleaner and more readable as follows:
```js
1  // ascending order
2  scores.sort((a, b) => a - b);
3  console.log(scores);
4  // [5, 9, 10, 20, 70, 80]
```
To sort an array of numbers numerically in descending order, you just need to reverse the logic in the compare function as shown in the following example:
```js
1  // descending order
2  scores.sort((a, b) => b - a);
3  console.log(scores);
4  // [80, 70, 20, 10, 9, 5] 
```

### Sorting an array of objects by a specified property

The following is an array of `employee` objects, where each object contains three properties: `name`,`salary` and `hireDate`.
```js
1  var employees = [    
2   {name: 'John', salary: 90000, hireDate: "July 1, 2010"},
3   {name: 'David', salary: 75000, hireDate: "August 15, 2009"},
4   {name: 'Ana', salary: 80000, hireDate: "December 12, 2011"}
5   ]; 
```

The following helper function outputs the `employees` array in the web console.
```js
1  function displayList(employees) {
2    employees.forEach(function (e) {
3        console.log('name:' + e.name +
4            ';salary:' + e.salary +
5            ';hireDate:' + e.hireDate);    
6    });
7  } 
```
#### Sorting objects by number property

The following example shows how to sort the employees by `salary` in ascending order.

| 123456 | // sort by salaryemployees.sort(function (x, y) {    return x.salary - y.salary;});// display the employee listdisplayList(employees); |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

This example is similar to the example of sorting an array of numbers in ascending order. The difference is that it compares the `salary` property of two objects instead.

#### Sorting objects by string property

To sort the `employees` array by `name` property case-insensitively, you pass the compare function that compares two strings case-insensitively as follows:

| 123456789101112 | employees.sort(function (x, y) {    var a = x.name.toUpperCase(),        b = y.name.toUpperCase();    if (a > b) {        return 1;    }    if (a < b) {        return -1;    }    return 0;});displayList(employees); |
| --------------- | ------------------------------------------------------------ |
|                 |                                                              |

#### Sorting objects by date property

Suppose, you wish to sort employees based on each employee’s hire date. The hire date data is stored in the `hireDate` property of the employee object. However, it is just a string that represents a valid date, not the `Date` object. Therefore, to sort employees by hire date, you first have to create a valid `Date`object from the date string, and then compare two dates, which is the same as comparing two numbers.

Here is the solution.

| 123456 | employees.sort(function (x, y) {    var a = new Date(x.hireDate),        b = new Date(y.hireDate);    return a - b;});displayList(employees); |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

### Optimizing JavaScript Array sort method

In fact, the `sort()` method calls the compare function multiple times for each element in the array. See the following example.

| 123456 | var rivers = ['Nile', 'Amazon', 'Congo', 'Mississippi', 'Rio-Grande']; rivers.sort(function (a, b) {    console.log(a, b);    return a.length - b.length;}); |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

1. First, declare an array `rivers` that consists of the famous river names.
2. Second, sort the `rivers` array by the length of its element using the `sort()` method. We output the elements of the `rivers` array to the web console whenever the `sort()` method invokes the compare function .

The following is the output in the web console:

| 123456 | Nile AmazonAmazon CongoNile CongoAmazon MississippiMississippi Rio-GrandeAmazon Rio-Grande |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

As shown above, each element has been evaluated multiple times e.g., Amazon 4 times, Congo 2 times, etc.

If the compare function has to do more work, it may yield a high overhead and potentially decreases the performance.

We cannot reduce the number of times that compare function is executed. However, we can reduce the work that the comparison has to do. This technique is called [Schwartzian Transform](http://en.wikipedia.org/wiki/Schwartzian_transform).

To implement this, you follow these steps:

1. First, extract the actual values into a temporary array using the [map()](http://www.javascripttutorial.net/javascript-array-map/) method.
2. Second, sort the temporary array with the elements that are already evaluated (or transformed).
3. Third, walk the temporary array to get an array with the right order.

Here is the solution.

| 12345678910111213141516171819 | // temporary array holds objects with position// and length of elementvar lengths = rivers.map(function (e, i) {    return {index: i, value: e.length };}); // sorting the lengths array containing the lengths of// river nameslengths.sort(function (a, b) {    return +(a.value > b.value) \|\| +(a.value === b.value) - 1;}); // copy element back to the arrayvar sortedRivers = lengths.map(function (e) {    return rivers[e.index];}); console.log(sortedRivers);// ["Nile", "Congo", "Amazon", "Rio-Grande", "Mississippi"] |
| ----------------------------- | ------------------------------------------------------------ |
|                               |                                                              |

In this tutorial, we have shown you how to use the JavaScript array sort() method to sort arrays of strings, numbers, and objects.

## Locating Elements: indexOf()

### JavaScript Array indexOf and lastIndexOf: Locating an Element in an Array

**Summary**: in this tutorial, we will show you how to use the JavaScript array `indexOf()` and `lastIndexOf()` methods to find the position of an element in an array.

### Introduction to the JavaScript array indexOf method

To find the position of an element in an [array](http://www.javascripttutorial.net/javascript-array/), you use the `indexOf()` method. This method returns the index of the first occurrence the element that you want to find, or -1 if the element is not found.

The following illustrates the syntax of the `indexOf()` method.

| 1    | Array.indexOf(searchElement, fromIndex) |
| ---- | --------------------------------------- |
|      |                                         |

As shown above, the `indexOf()` method accepts two named arguments.

1. The `searchElement `argument is the element that you want to find in the array.
2. The `fromIndex` is an array index at which the function starts the search.

The `fromIndex` argument can be a positive or negative integer. If the `fromIndex` argument is negative, the `indexOf()` method starts searching at array’s length plus `fromIndex`.

In case you omit the `fromIndex` argument, the `indexOf()` method starts searching from the element 0.

Notice that the `indexOf()` method uses the [strict equality comparison algorithm](http://www.ecma-international.org/ecma-262/5.1/#sec-11.9.6) that is similar to the triple-equals operator (===) when comparing the `searchElement` with the elements in the array.

### The JavaScript array indexOf method examples

Suppose, you have an array `scores` that consists of six numbers as follows.

| 1    | var scores = [10, 20, 30, 10, 40, 20]; |
| ---- | -------------------------------------- |
|      |                                        |

The following example uses the `indexOf()` method to find the elements in the `scores` array.

| 1234 | console.log(scores.indexOf(10)); // 0console.log(scores.indexOf(30)); // 2console.log(scores.indexOf(50)); // -1console.log(scores.indexOf(20)); // 1 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

![JavaScript Array indexOf Method Example](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Array-Find-indexOf-Method-Example.png)

Also, the following example uses the `fromIndex` with the negative values.

| 12   | console.log(scores.indexOf(20,-1)); // 5 (fromIndex = 6+ (-1) = 5)console.log(scores.indexOf(20,-5)); // 1 (fromIndex = 6+ (-5) = 1) |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Assuming that you have the following array of objects, where each object has two properties: `name` and `age`.

| 12345 | var guests = [    {name: 'John Doe', age: 30},    {name: 'Lily Bush', age: 20},    {name: 'William Gate', age: 25}]; |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

The following statement returns -1 even though the first element of the `guests` array and the `searchElement` have the same values in the `name` and `ages` properties. This is because they are two different objects.

| 1234 | console.log(guests.indexOf({    name: 'John Doe',    age: 30})); // -1 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Sometimes, you want to find the indices of all occurrences of an element in an array. The following `find()` function uses the `indexOf()` method to do so.

| 123456789 | function find(needle, haystack) {    var results = [];    var idx = haystack.indexOf(needle);    while (idx != -1) {        results.push(idx);        idx = haystack.indexOf(needle, idx + 1);    }    return results;} |
| --------- | ------------------------------------------------------------ |
|           |                                                              |

The following example uses the `find()` function above to return an array of positions of the number 10 in the `scores` array.

| 1    | console.log(find(10,scores)); // [0, 3] |
| ---- | --------------------------------------- |
|      |                                         |

### JavaScript array lastIndexOf method

The [Array](http://www.javascripttutorial.net/javascript-array/) type has another method called `lastIndexOf()` that provides the similar functionality to the `indexOf()` method.

The following illustrates the syntax of the `lastIndexOf()` method.

| 1    | Array.lastIndexOf(searchElement[, fromIndex = Array.length - 1]) |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

The `lastIndexOf()` method returns the index of the last occurrence of the `searchElement` in the array. It returns – 1 if it cannot find the element.

Different from the `indexOf()` method, the `lastIndexOf()` method searches for the element backward, starting at `fromIndex.`

The following statements return the last indices of the number 10 and 20 in the `scores` array.

| 12   | console.log(scores.lastIndexOf(10));// 3console.log(scores.lastIndexOf(20));// 5 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

![JavaScript Array lastIndexOf Method Example](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Array-Find-lastIndexOf-Method-Example.png)

Because the number 50 is not in the `scores` array, the following statement returns -1.

| 1    | console.log(scores.lastIndexOf(50));// -1 |
| ---- | ----------------------------------------- |
|      |                                           |

In this tutorial, you have learned how to use the JavaScript array `indexOf()` and `lastIndexOf()`methods to locate an element in the array.

## Testing Elements: every() & some()

### JavaScript Array Every: Testing Array Elements

**Summary**: in this tutorial, you will learn how to check whether all or some array elements match specified criteria by using the JavaScript `every()` and `some()` methods.

### Checking every element using a for loop

Sometimes, you need to test whether every element of an [array](http://www.javascripttutorial.net/javascript-array/) satisfies a specific condition. Typically, you use a  [`for `loop](http://www.javascripttutorial.net/javascript-for-loop/) to iterate all elements and check each individual element against a test condition. See the following example.

Suppose you have an array `numbers` with three elements.

| 1    | var numbers = [1, 3, 5]; |
| ---- | ------------------------ |
|      |                          |

To check if all the elements of the `numbers` array are greater than zero, you use the following code.

| 12345678 | var result = true;for (var i = 0; i < numbers.length; i++) {    if (numbers[i] <= 0) {        result = false;        break;    }}console.log(result); // true |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

How it works.

- First, initialize the  `result` variable to `true`.
- Second, loop over the elements of the `numbers` array and check whether each element is less than or equal zero. If it is the case, we set the `result` variable to `false` and terminate the loop immediately using the [`break`](http://www.javascripttutorial.net/javascript-break/) statement. In case no element is less than or equal zero, the value of the `result` variable remains intact i.e. `true`.

This code is simple and straight forward. However, JavaScript `Array` type provides the `every()` method that allows us to complete this kind of tasks in a much cleaner way.

### Introduction to JavaScript array every() method

Starting from ES5, [JavaScript Array](http://www.javascripttutorial.net/javascript-array/) type provides a method `every()` that tests every element in an array. The following example uses the `every()` method that is equivalent to the script above.

| 1234 | var result = numbers.every(function (e) {    return e > 0;});console.log(result); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

It is nice, isn’t it?

The following illustrates the syntax of the `every()` method.

| 1    | Array.every(callback[, contextObject]) |
| ---- | -------------------------------------- |
|      |                                        |

The `every()` method accepts two named arguments: `callback` and `thisArg`.

The `callback` argument is a function that tests each element of the array. The `callback()` function has the following form.

| 123  | function callback(currentElement, index, array){   //...} |
| ---- | --------------------------------------------------------- |
|      |                                                           |

The `callback` function takes three arguments:

1. First, the `currentElement` is the current element being processed.
2. Second, the `index` is the index  of the `currentElement`.
3. Third, the `array` is the array that the `every()` method was called upon.

The `currentElement` argument is required whereas the `index` and `array` arguments are optional.

The `contextObject` argument of the `every()` method is optional. If you pass in the `contextObject`argument, the `this` object inside the `callback()` function refers to the `contextObject` argument.

The `every()` method returns `true` if the `callback` function returns a truthy value for every array element; otherwise, it returns `false`.

Note that the `every()` method executes the `callback()` function on every element in the array until it finds one where the `callback()` function returns a *falsy* value.

Let’s take a look at some more examples that use the `every()` method.

### More JavaScript every() method examples

The following example tests whether all elements in the `numbers` array are the even numbers

| 1234 | var isEven = numbers.every(function (e) {    return e % 2 == 0;});console.log(isEven); // false |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

In contrast, the following example tests if all elements in the `numbers` array are the odd numbers.

| 1234 | var isOdd = numbers.every(function (e) {    return Math.abs(e % 2) == 1;});console.log(isOdd);// true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Assuming that we have an object with two properties: `minimum` and `maximum`.

| 1234 | var oneToTen = {    minimum: 0,    maximum: 10}; |
| ---- | ------------------------------------------------ |
|      |                                                  |

The following example tests whether all elements in the `numbers` array are in the range specified by the `minium` and `maximum` of the `oneToTen` object.

| 1234 | var isInRange = numbers.every(function (e) {    return e >= this.minimum && e <= this.maximum;}, oneToTen);console.log(isInRange); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

As you see above, we pass the `oneToTen` object to the `every()` method as the second argument and inside the `callback()` function, we reference to the `oneToTen` object using the `this` keyword.

### JavaScript array some() method

The `Array` type also provides the `some()` method that is similar to the `every()` method. The `some()`method executes a `callback` function on every element in the array and returns `true` if the `callback`function returns `true` for any item.

Suppose you have a `scores` array with three numbers as follows.

| 1    | var scores = [10, 15, 20]; |
| ---- | -------------------------- |
|      |                            |

To check if some of the numbers in the `scores` array are the odd numbers, you use the `some()`method as follows:

| 1234 | var someOdd = scores.some(function (e) {    return Math.abs(e % 2) == 1;});console.log(someOdd); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Note that the `some()` method executes the `callback()` function on every element in the array until it finds one where the `callback` function returns a truthy value.

See the following example.

| 123456789101112131415 | var colors = ['red', 'green', 'blue'];var counter = 0;var greenExist = colors.some(function (e) {    counter++;    console.log(counter);    return e === 'green';});console.log(greenExist);console.log(counter);  // --- output in web console//1//2//true//2 |
| --------------------- | ------------------------------------------------------------ |
|                       |                                                              |

We use the `some()` method to check if the ‘`green'` string exists in the `colors` array. As shown in the web console, the `some()` method executes the callback function twice until it finds the ‘green’ element.

In this tutorial, you have learned how to test every element or some elements in an array if they match a specified condition by using the JavaScript `every()` and `some()` methods of the array object.

## Filtering Array Elements: filter()

### JavaScript Array Filter: Filtering Elements

**Summary**: in this tutorial, you will learn how to use the JavaScript Array filter() method to filter elements in an array.

### Introduction to JavaScript array filter method

One of the most common tasks when working with an [array](http://www.javascripttutorial.net/javascript-array/) is to create a new array that contains a subset of elements of the original array.

Suppose you have an array of `city` objects where each object contains two properties: `name` and `population`.

| 1234567 | var cities = [    {name: 'Los Angeles', population: 3792621},    {name: 'New York', population: 8175133},    {name: 'Chicago', population: 2695598},    {name: 'Houston', population: 2099451},    {name: 'Philadelphia', population: 1526006}]; |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

To find the city whose population is greater than 3 million, you typically loop over the array using a [for loop](http://www.javascripttutorial.net/javascript-for-loop/) and test if the value of the `population` property satisfies the condition as shown in the following code:

| 1234567 | var bigCities = [];for (var i = 0; i < cities.length; i++) {    if (cities[i].population > 3000000) {        bigCities.push(cities[i]);    }}console.log(bigCities); |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

Fortunately, JavaScript Array provides the `filter()` method that allows us to do this kind of tasks in a shorter and cleaner way.

The following example returns the same result as the code above.

| 1234 | var bigCities = cities.filter(function (e) {    return e.population > 3000000;});console.log(bigCities); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

We call the `filter()` method of the `cities` array object and pass in a function that tests each element. Inside the function, we check if the `population` of the each element in the array is greater than 3 million. If it is the case, the function returns `true`; Otherwise, it returns `false`. The `filter()`method will include only the element in the resulting array if the element satisfies the test in the function that we pass in.

By the way, in ES6, it is even cleaner when you use the arrow function (=>).

| 12   | var bigCities = cities.filter(e => e > 3000000);console.log(bigCities); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

### JavaScript Array filter method in detail

The following illustrates the syntax of the `filter()` method.

| 1    | Array.filter(callback, contextObject); |
| ---- | -------------------------------------- |
|      |                                        |

The `filter()` method creates a new array by filtering out all the elements that do not pass the test implemented by the `callback()` function. Internally, the `filter()` method iterates over each element of an array and pass each element to the `callback()` function. If the `callback()` function returns `true`, the element is included in the resulting array.

The `filter()` method accepts two named arguments: a `callback()` function and an optional object.

Like other iterative methods of the Array object such as `every(),` `some(),` [`map()`](http://www.javascripttutorial.net/javascript-array-map/) and `forEach(),` the `callback()` function has the following form:

| 123  | function callback(currentElement, index, array){   // ...} |
| ---- | ---------------------------------------------------------- |
|      |                                                            |

The `callback()` function takes 3 arguments:

1. The `currentElement` argument is the current element in the array that is being processed by the `callback` function.
2. The `index` of the `currentElement` that is being processed by the `callback` function.
3. The `array` object being traversed.

The `index` and `array` arguments are optional.

The `contexObject` argument of the `filter()` method is optional. If you pass this object, you are able to reference it by using `this` keyword inside the `callback()` function.

It is import to note that the `filter()` method does not change the original array.

### More JavaScript array filter method examples

Because the `filter()` method returns an array, you can chain the result with other iterative methods such as `sort()` and `map().` For example, the following illustrates how to chain three methods:

For example, the following illustrates how to chain three methods: `filter(),``sort(),` and `map():`

| 1234567 | cities.filter(function (e) {    return e.population < 3000000;}).sort(function (a, b) {    return b.population - a.population;}).map(function (e) {    console.log(e.name + ':' + e.population);}); |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

 

 

| 123  | cities.filter(e => e.population < 3000000)    .sort((a, b) => (b.population - a.population))    .map(e => console.log(e.name + ':' + e.population)); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

 

1. First, the `filter()` method returns the cities whose populations are less than 3 million.
2. Second, the [`sort()`](http://www.javascripttutorial.net/javascript-array-sort/) method sorts the resulting cities by the population in descending order
3. Third, the `map()` method logs each element in the resulting array in the web console.

The following example uses the arrow functions that provide the same result as the example above.

| 123  | cities.filter(e => e.population < 3000000)       .sort((a, b) => (b.population - a.population))      .map(e => console.log(e.name + ':' + e.population)); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

The following example illustrates the use of the `contextObject` argument that specifies an object which can be referenced in the `callback()` function using the `this` keyword.

| 1234567891011121314 | function isInRange(value) {    if (typeof value !== 'number') {        return false;    }    return value >= this.lower && value <= this.upper;} var data = [10, 20, "30", 1, 5, 'JavaScript filter', undefined, 'example']; var range = {lower: 1, upper: 10}; var numberInRange = data.filter(isInRange, range); console.log(numberInRange); // [10, 1, 5] |
| ------------------- | ------------------------------------------------------------ |
|                     |                                                              |

How it works.

- First, define the `isInRange()` function that checks if its argument is a number and in a range that specifies by the `lower` and `upper` properties of an object.
- Next, define an array of mixed data that contains [numbers](http://www.javascripttutorial.net/javascript-data-types/#number), [strings](http://www.javascripttutorial.net/javascript-data-types/#string), and [undefined](http://www.javascripttutorial.net/javascript-data-types/#undefined).
- Then, define the `range` object with two properties `lower` and `upper`.
- After that, call the `filter()` methods of the `data` array and pass in the `isInRange()` function and the `range `object. Because we pass in the `range` object, inside the `isInRange()` function, the `this` keyword references to the `range` object.
- Finally, log the resulting array in the web console.

In this tutorial, you have learned how to use the JavaScript array filter method to filter elements in an array based on a test provided by a callback function.

## Reducing an Array Into a Value: reduce()

### JavaScript Array reduce & reduceRight: Reducing an Array Into a Value

**Summary**: in this tutorial, you will learn how to use the JavaScript array reduce and reduceRight method to reduce an array to a value.

### Introduction to the JavaScript array reduce method

Whenever you need to reduce an [array](http://www.javascripttutorial.net/javascript-array/) into a value, you typically use a [`for` loop](http://www.javascripttutorial.net/javascript-for-loop/) as shown in the following example.

| 1234567 | var numbers = [1, 2, 3]; var sum = 0;for (var i = 0; i < numbers.length; i++) {    sum += i;}console.log(sum); // 6 |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

The script is simple and straightforward.

1. First, decalre an array of three numbers 1, 2 and 3.
2. Second declare the `sum` [variable](http://www.javascripttutorial.net/javascript-variables/) and assign it zero.
3. Third, in the `for` loop, add up the elements of the `numbers` array to the `sum` variable. After the loop, the value of the `sum` variable is 6.

What we have done was to **reduce** the `numbers` array into the `sum` variable.

The `Array` type provides a method named `reduce()` that helps you to process these kind of tasks. See the following code.

| 1234 | var sum = numbers.reduce(function (prev, curr) {    return prev + curr;});console.log(sum); // 6 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

It’s pretty simple, isnt’ it?

Let’s take a look at the `reduce()` method in detail.

### JavaScript array reduce in detail

The following illustrates the syntax of the `reduce()` method.

| 1    | Array.reduce(callback[, initialValue]) |
| ---- | -------------------------------------- |
|      |                                        |

The `reduce()` method takes two arguments: a `callback()` function and an initial value.

The `redude()` method calls the `callback()` function for every element in an array. The `callback()`function returns a value that is the accumulated result, and this result is provided as an argument in the next call to the `callback()` function.

#### The callback function

The `callback()` function has the following form:

| 1    | function callback(previousValue, currentValue, currentIndex, array){} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

The `calback()` method takes four arguments listed in the following table:

| Argument        | Definition                                                   |
| --------------- | ------------------------------------------------------------ |
| `previousValue` | The value returned from the previous call of the `callback()` function. If you pass the `initialValue` to `the reduce()` method,  when the callback function is called at the first time, the `previousValue` equals `initialValue`. |
| `currentValue`  | The value of the current element being processed in the array |
| `currentIndex`  | The index of the current element being processed in the array. |
| `array`         | The array that the `reduce()` method was called upon.        |

#### The initialValue argument

This argument is optional. If you pass in the `initialValue` argument, the `reduce()` method will assign it to the `previousValue` argument of the `callback()` function at the first call of the `callback()` function.

The following table illustrates the logic when the `reduce()` method calls the `callback()` function at the first time according to the `initialValue` argument.

| `initialValue` | `previousValue`                | `currentValue`            |
| -------------- | ------------------------------ | ------------------------- |
| passed         | `previousValue = initialValue` | `currentValue = array[0]` |
| not passed     | `prevousValue = array[0]`      | `currentValue = array[1]` |

Back to the example above, the following table illustrates how the `reduce()` method works in detail.

| 1234 | var sum = numbers.reduce(function (prev, curr) {    return prev + curr;});console.log(sum); // 6 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

|          | `previousValue` | `currentValue` | `currentIndex` | `currentIndex` | return Value |
| -------- | --------------- | -------------- | -------------- | -------------- | ------------ |
| 1st call | 0               | 1              | 0              | [1, 2, 3]      | 1            |
| 2nd call | 1               | 2              | 1              | [1, 2, 3]      | 3            |
| 3rd call | 3               | 3              | 2              | [1, 2, 3]      | 6            |

### More JavaScript array reduce examples

Suppose, we have a `shoppingCart` array of product objects as follows.

| 12345 | var shoppingCart = [    {name: 'phone', qty: 1, price: 699},    {name: 'Screen Protector', qty: 1, price: 9.98},    {name: 'Memory Card', qty: 2, price: 20.99}]; |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

To calculate the total amount of the products in the shopping cart, you can use the `reduce()` method as shown in the code below.

| 12345 | var total = shoppingCart.reduce(function (prev, curr) {    return prev + curr.qty * curr.price;},0); console.log(total); // 750.96 |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

Notice that in this example, we passed in the `initialValue` argument to the `reduce()` method. If we didn’t, the `reduce()` method would take the first element of the `shoppingCart` array, which is an object, as an initial value and perform the calculation on this object. Hence, it would cause an incorrect result.

### JavaScript array reduceRight method

The `reduceRight()` method works in the samw way as the `reduce()` method, just in the opposite direction.

The `reduce()` method starts at the first element and travels toward the last, whereas the `reduceRight()` method starts at the last element and travels toward the first.

See the following example.

| 1234 | var sum2 = numbers.reduceRight(function (prev, curr) {    return prev + curr;});console.log(sum2); // 6 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

In this example, `prev` is 5 and `curr` is 4 at the first time the `callback()` function is executed.

The following picture illustrates the difference between the `reduce()` and `reduceRight()` methods.

![JavaScript array reduce vs reduceRight](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-array-reduce-vs-reduceRight.png)

In this tutorial, we have shown you how to use the JavaScript array `reduce()` and `reduceRight()`methods to reduce an array into a value.

## Executing a Callback on Elements: forEach()

### JavaScript Array forEach: Executing a Function on Every Element

**Summary**: in this tutorial, you will learn how to use the JavaScript Array forEach method to run a function on every element in an array.

### Introduction to JavaScript Array forEach method

Typically, when you want to execute a [function](http://www.javascripttutorial.net/javascript-function/) on every element of an [array](http://www.javascripttutorial.net/javascript-array/), you use a [for](http://www.javascripttutorial.net/javascript-for-loop/) loop statement. For example, the following code outputs every element of an array in the web console, each element per line.

| 1234567 | var ranks = ['A', 'B', 'C'];for (var i = 0; i < ranks.length; i++) {    console.log(ranks[i]);}// A// B// C |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

JavaScript Array provides the `forEach()` method that allows you to run a function on every element. The following code uses the `forEach()` method that is equivalent to the code above.

| 123  | ranks.forEach(function (e) {    console.log(e);}); |
| ---- | -------------------------------------------------- |
|      |                                                    |

The `forEach()` method iterates over elements in an array and executes a predefined function once per element. The following illustrates the syntax of the `forEach()` method.

| 1    | Array.forEach(callback [, contextObject]); |
| ---- | ------------------------------------------ |
|      |                                            |

The `forEach()` method takes two arguments.

1. The `callback` function that the `forEach()` method uses to execute on every element
2. The `contextObject` used for the `callback` function, meaning that you can refer to the `contextObject` inside the `callback` function using the `this` keyword.

Note that the `forEach()` function returns undefined therefore it is not chainable like other iterative methods: `filter(),` `map(),` `some(),` `every(),` and `sort().`

One limitation of the `forEach()` method in comparison with the `for` loop is that you cannot use the [break](http://www.javascripttutorial.net/javascript-break/) or [continue](http://www.javascripttutorial.net/javascript-continue/) statement to control the loop. To terminate the loop in the `forEach()` method, you must throw an exception inside the `callback` function.

### More JavaScript Array forEach method example

Let’s take a look at an example of the `forEach()` method that uses a `contextObject`.

The following illustrates `Counter` constructor function.

| 123456789101112131415 | function Counter() {    this.count = 0;    var self = this;    return {        increase: function () {            self.count++;        },        current: function () {            return self.count;        },        reset: function () {            self.count = 0;        }    }} |
| --------------------- | ------------------------------------------------------------ |
|                       |                                                              |

This example shows how to pass the counter object to the `forEach()` method.

| 12345678910 | var counter = new Counter();var numbers = [1, 2, 3];var sum = 0;numbers.forEach(function (e) {    sum += e;    this.increase();}, counter); console.log(sum); // 6console.log(counter.current()); // 3 |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

How it works.

- First, create a new Counter object.
- Next, define an array of three numbers.
- Then, declare a variable sum and assign it a value of zero.
- After that, call the `forEach()` method on the `numbers` array. In the callback function, add the element to the `sum` variable and call the `increase()` method of the `counter` object. Notice that the `counter` object is referred to as `this` inside the callback function.
- Finally, log the value of the sum and current value of the counter in the web console.

In this tutorial, you have learned how to use the JavaScript Array forEach method to execute a provided function on every element of an array.

## Transforming Array Elements: map()

### Essential Guide to JavaScript Map: How To Use Maps Effectively

**Summary**: in this tutorial, we will introduce you to the JavaScript Map object that allows you to map a key to a value.

### Introduction to JavaScript Map object

Prior ES6, when you need to map keys to values, you often use an object, because objects allow you to map key to values of any type.

However, using objects as maps has some side effects.

1. An Object always has default keys in the map because it has a prototype.
2. Keys of an object must be strings or symbols, you cannot use Objects as keys.
3. An Object does not have a property that represents the size of the map.

ES6 provides the Map that addresses these deficiencies.

By definition, a Map object is a key-value map where a value of any type can be used as either a key or a value.

To create a new Map, you use the following syntax:

| 1    | let map = new Map([iterable]); |
| ---- | ------------------------------ |
|      |                                |

The `Map()` constructor accepts an optional iterable object such as an [Array](http://www.javascripttutorial.net/javascript-array/).

### JavaScript Map example

Suppose you have a list of user objects as follows:

| 123  | let john = {name: 'John Doe'},    lily = {name: 'Lily Bush'},    peter = {name: 'Peter Drucker'}; |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Assuming that you have to create a map of users and roles. In this case, you use the following code.

| 1    | let userRoles = new Map(); |
| ---- | -------------------------- |
|      |                            |

The `userRoles` variable is an instance of the Map object and its type is an object as illustrated in the following example.

| 12   | console.log(typeof(userRoles)); // objectconsole.log(userRoles instanceof Map); // true |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

To assign a user to a role, you use the `set()` method.

| 1    | userRoles.set(john, 'admin'); |
| ---- | ----------------------------- |
|      |                               |

The `set()` method maps user `john` with the `admin` role. Because, the `set()` method is chainable, you can save some typing as shown in this example.

| 12   | userRoles.set(lily, 'editor')          .set(peter, 'subscriber'); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

As mentioned earlier, you can pass an iterable object to the `Map()` constructor:

| 12345 | let userRoles = new Map([    [john, 'admin'],    [lily, 'editor'],    [peter, 'subscriber']]); |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

If you want to see what role that John has, you use the `get()` method:

| 1    | userRoles.get(john); // admin |
| ---- | ----------------------------- |
|      |                               |

If you pass a key that is not in the map, the `get()` method will return undefined.

| 12   | let foo = {name: 'Foo'};userRoles.get(foo); //undefined |
| ---- | ------------------------------------------------------- |
|      |                                                         |

To check if a key exists in the map, you use the `has()` method.

| 12   | userRoles.has(foo); // falseuserRoles.has(lily); // true |
| ---- | -------------------------------------------------------- |
|      |                                                          |

The size property returns the number of entries in the map.

| 1    | console.log(userRoles.size); // 3 |
| ---- | --------------------------------- |
|      |                                   |

To get the keys of a map object, you use the `keys()` method. The `keys()` method returns a new iterator object that contains the keys of elements in the map.

The following example displays username of the users in the userRoles map object.

| 123456 | for (let user of userRoles.keys()) {    console.log(user.name);}// John Doe// Lily Bush// Peter Drucker |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

Similarly, you can use the `keys()` method to get an iterator object that contains keys for all elements in the Map.

| 123456 | for (let role of userRoles.values()) {    console.log(role);}// admin// editor// subscriber |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

Also, the `entries()` method returns an iterator object that contains an array of `[key,value]` of each element in the Map object.

| 1234567 | for (let elem of userRoles.entries()) {    console.log(`${elem[0].name}: ${elem[1]}`);} // John Doe: admin// Lily Bush: editor// Peter Drucker: subscriber |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

To make the iteration more natural, you can use destructuring as follows.

| 123  | for (let [user,role] of userRoles.entries()) {    console.log(`${user.name}: ${role}`);} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

In addition to for…of loop, you can use the `forEach()` method of the map object.

| 123  | userRoles.forEach((role, user) =>    console.log(`${user.name}: ${role}`)); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Sometimes, you want to work with an array instead of an iterable object, in this case, you can use the [spread operator](http://www.javascripttutorial.net/es6/javascript-spread/) as follows:

| 12   | var roles = [...userRoles.values()];console.log(roles); // ["admin", "editor", "subscriber"] |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

To delete an entry in the map, you use the `delete()` method.

| 1    | userRoles.delete(john); |
| ---- | ----------------------- |
|      |                         |

To delete all entries in the map object, you use the `clear()` method.

| 1    | userRoles.clear(); |
| ---- | ------------------ |
|      |                    |

Hence, the size of the map now is zero.

| 1    | console.log(userRoles.size); // 0 |
| ---- | --------------------------------- |
|      |                                   |

### WeakMap

A `WeakMap` is identical to Map except for the following features:

1. Keys of a `WeakMap` must be objects.
2. Keys of a `WeakMap` are weak, meaning that they may be garbage-collected.

A `WeakMap` only has a subset methods of a `Map`, and its elements cannot be iterated.

In this tutorial, you have learned how to work with the JavaScript Map object and its useful methods to manipulate entries in the map.

## JavaScript Multidimensional Array

### JavaScript Multidimensional Array

**Summary**: in this tutorial, you will learn how to work with JavaScript multidimensional array.

### Introduction to JavaScript multidimensional array

JavaScript does not provide the multidimensional array natively. However, you can create a multidimensional array by defining an [array](http://www.javascripttutorial.net/javascript-array/) of elements, where each element is also another array. For this reason, we can say that a JavaScript multidimensional array is an array of arrays.

The easiest way to define a multidimensional array is to use the array literal notation. The following example defines two-dimensional array named `activities`.

| 1234567 | var activities = [    ['Work', 9],    ['Eat', 2],    ['Commute', 2],    ['Play Game', 2],    ['Sleep', 7]]; |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

In the `activities` array, the first dimension represents the activity and the second one shows the number of hours spent per day for each.

The following figure illustrates the `activities` array:

![JavaScript Multidimensional Array Example](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-Multidimensional-Array-Example.png)

To access an element of the multidimensional array, you first use square brackets to access an element of the outer array which returns an inner array; and the use another square bracket to access the element of the inner array.

The following example returns the second element of the first inner array in the `activities` array above.

![Accessing JavaScript Multidimensional Array Element](http://www.javascripttutorial.net/wp-content/uploads/2016/08/Accessing-an-JavaScript-Multidimensional-Array-Element.png)

| 1    | console.log(activities[0][1]); // 9 |
| ---- | ----------------------------------- |
|      |                                     |

### Adding an element to the JavaScript multidimensional array

You can use the array methods to manipulate a multidimensional array as normal. For example, to add a new element to a multidimensional array, you use the `push()` method as in the following example.

| 1    | activities.push(['Study',2]); |
| ---- | ----------------------------- |
|      |                               |

![Adding an Element to JavaScript Multidimensional Array](http://www.javascripttutorial.net/wp-content/uploads/2016/08/Adding-an-Element-to-JavaScript-Multidimensional-Array.png)

This example calculates the percentage of the hours spent for each activity and append the percentage to the inner array.

| 12345 | for (var i = 0; i < activities.length; i++) {    var percentage = ((activities[i][1] / 24) * 100).toFixed();    activities[i][2] = percentage + '%';}console.log(activities.join('\n')); |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

The following shows the output in the web console.

| 123456 | Work,9,38%Eat,2,8%Commute,2,8%Play Game,2,8%Sleep,7,29%Date,2,8% |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

![Adding elements to the inner array](http://www.javascripttutorial.net/wp-content/uploads/2016/08/Adding-elements-to-the-inner-array.png)

### Removing an element from the JavaScript multidimensional array

To remove an element from an array, you use the `pop()` method`.`For example, the following statement removes the last element of the `activities` array.

| 12   | activities.pop();console.log(activities.join('\n')); |
| ---- | ---------------------------------------------------- |
|      |                                                      |

The output of the script in the web console is as follows:

| 12345 | Work,9,38%Eat,2,8%Commute,2,8%Play Game,2,8%Sleep,7,29% |
| ----- | ------------------------------------------------------- |
|       |                                                         |

![Removing an Element from JavaScript Multidimensional Array](http://www.javascripttutorial.net/wp-content/uploads/2016/08/Removing-an-Element-from-JavaScript-Multidimensional-Array.png)

Similarly, you can remove the elements from the inner array of the multidimensional array by using the `pop()` method.

Here is an example of removing the percentage element from the inner arrays of the `activities` array.

| 1234 | for (var i = 0; i < activities.length; i++) {    activities.pop(2);}console.log(activities.join('\n')); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

| 12345 | Work,9Eat,2Commute,2Play Game,2Sleep,7 |
| ----- | -------------------------------------- |
|       |                                        |

### ![Removing Elements from JavaScript Multidimensional Array](http://www.javascripttutorial.net/wp-content/uploads/2016/08/Removing-Elements-from-JavaScript-Multidimensional-Array.png)

### Iterating a JavaScript multidimensional array

To iterate a multidimensional array, you use a nested [for loop](http://www.javascripttutorial.net/javascript-for-loop/) as in the following example.

| 123456789 | // loop the outer arrayfor (var i = 0; i < activities.length; i++) {    // get the size of the inner array    var innerArrayLength = activities[i].length;    // loop the inner array    for (var j = 0; j < innerArrayLength; j++) {        console.log('[' + i + ',' + j + '] = ' + activities[i][j]);    }} |
| --------- | ------------------------------------------------------------ |
|           |                                                              |

The first loop iterates over the elements of the outer array, while the nested one iterates over the inner array.

![Looping a JavaScript Multidimensional Array](http://www.javascripttutorial.net/wp-content/uploads/2016/08/Looping-a-JavaScript-Multidimensional-Array.png)

The following shows the output of the script in the web console.

| 12345678910 | [0,0] = Work[0,1] = 9[1,0] = Eat[1,1] = 2[2,0] = Commute[2,1] = 2[3,0] = Play Game[3,1] = 2[4,0] = Sleep[4,1] = 7 |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

In this tutorial, you have learned how to use an array of arrays to create a JavaScript multidimensional array.