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

| 1    | var scores = new Array(); |
| ---- | ------------------------- |
|      |                           |

The `scores` array is empty i.e. it holds no element.

If you know the number of elements that the array will hold, you can create an array with an initial size as in the following example:

| 1    | var scores = Array(10); |
| ---- | ----------------------- |
|      |                         |

To create an array with initial elements, you pass the elements as a comma-separated list in the `Array()` constructor. The following example creates the `scores` array that holds five numbers:

| 1    | var scores = new Array(9,10,8,7,6); |
| ---- | ----------------------------------- |
|      |                                     |

It’s important to notice that if you use the array constructor to create an array and pass in a number, you are creating an array with an initial size. However, if you pass in one argument of another type, you create an array that holds that element.