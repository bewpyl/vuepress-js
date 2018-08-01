---
sidebar: auto
---

# Control Flow

## JavaScript if else Statement

**Summary**: in this tutorial, you will learn how to use the JavaScript `if else` statement to execute a statement based on a specified condition.

### Introduction to the JavaScript if else statement

The `if` statement is probably one of the most frequently used statements in JavaScript. The `if`statement executes a statement or block of code if a condition is satisfied.

The following is the simple form of the `if` statement.

| 12   | if( condition )   statement; |
| ---- | ---------------------------- |
|      |                              |

The condition can be any expression. In general, the condition evaluates to a [Boolean](http://www.javascripttutorial.net/javascript-data-types/#boolean) value, either `true` or `false`. In case the condition evaluates to a non-Boolean value, JavaScript automatically converts its result into a Boolean value by calling the [`Boolean()`](http://www.javascripttutorial.net/javascript-boolean/) function on it.

If the condition evaluates to `true`, the statement is executed. Otherwise, the control is passed to the next statement that follows the `if` statement.

The following flowchart illustrates the `if` statement.

![JavaScript if statement](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-if-statement.png)