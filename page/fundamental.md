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