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

The following example illustrates how to use the `if` statement:

| 123  | var x = 25;if(x > 10)    console.log('x is greater than 10'); |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

It first initializes the variable `x` to `25`.  The `x > 10` expression evaluates to `true`, therefore the script logs a message to the web console.

In case you have more than one statement to execute, you need to use curly braces as follows:

| 123  | if(condition) {// statements} |
| ---- | ----------------------------- |
|      |                               |

It is a good programming practice to always use the curly braces even if there is only one statement to be executed. It helps the code easier to read and avoid many confusions.

See the following example.

| 123  | if( condition )   statement_1   statement_2; |
| ---- | -------------------------------------------- |
|      |                                              |

If you don’t use the curly braces, it is difficult to see that the `statement_2` does not belong to the if block.

In case you want to execute anther statement when the condition evaluates to `false`, you use the `else` as follows:

| 12345 | if(condition) {  // statement} else {   // statement (when condition evaluates to false)} |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

The following flowchart illustrates the `if else` statement.

![JavaScript if else statment](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-if-else-statment.png)

See the following example.

| 123456 | var x = 5;if (x > 10) {    console.log('x is greater than 10');} else {    console.log('x is less than or equal 10');} |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

You can chain the `if else` statements as follows:

| 1234567 | if (condition_1) {   // statments} else if (condition_2) {  // statments} else {   // statments} |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

For example, the following script compares two numbers `a` and `b,` returns the corresponding message if `a` is greater than, less than, or equal to `b`.

| 12345678 | var a = 10, b = 20;if (a > b) {    console.log('a is greater than b');} else if (a < b) {    console.log('a is less than b');} else {    console.log('a is equal to b');} |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

If you chain many `if else` statements, the code will become hard to read and difficult to maintain. In such situations, you should use the [`switch`](http://www.javascripttutorial.net/javascript-switch-case/) statement.

### JavaScript if else shortcut: conditional operator

JavaScript provides a conditional operator that can be used as a shortcut of the `if` statement. The following illustrates the syntax of the conditional operator.

| 1    | condition ? expression_1 : expression_2 |
| ---- | --------------------------------------- |
|      |                                         |

Like the `if` statement, the `condition` is an expression that evaluates to `true` or `false`. If the condition evaluates to `true`, the operator returns the value of the `expression_1`; otherwise, it returns the value of the `expression_2`.

For example, to display a different label for the login button based on the value of the `isLoggedIn`variable, you could use the conditional operator as follows:

| 1    | isLoggedIn ? : "Logout" : "Login"; |
| ---- | ---------------------------------- |
|      |                                    |

You can also assign a variable depending on the result of the ternary operator.

| 12   | // only register if the age is greater than 18var allowRegister = age > 18 ? true : false; |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

If you want to do more than a single operation per case, you need to separate operation using a comma (,) as the following example:

| 1234567 | age > 18 ? (    alert("OK, you can register."),    redirectTo("register.html");) : (    stop = true,    alert("Sorry, you are too young!")); |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

In this tutorial, you have learned how to use the JavaScript `if else` statement to execute a statement when a condition evaluates to true and executes another statement when the condition evaluates to false.

## JavaScript switch case

**Summary**: in this tutorial, you will learn how to use the JavaScript switch case statement to control complex conditional operations.

### Introduction to the JavaScript switch case statement

The `switch` statement is a flow-control statement that is similar to the [`if else`](http://www.javascripttutorial.net/javascript-if-else/) statement. You use the `switch` statement to control the complex conditional operations.

The following illustrates the syntax of the `switch` statement:

| 12345678910111213 | switch (expression) {    case value_1:        statement_1;        break;    case value_2:        statement_2;        break;    case value_3:        statement_3;        break;    default:        default_statement;} |
| ----------------- | ------------------------------------------------------------ |
|                   |                                                              |

Each case in the `switch` statement executes the corresponding statement ( `statement_1`, `statement_2`,…) if the `expression` equals the value ( `value_1`, `value_2`, …).

The [`break`](http://www.javascripttutorial.net/javascript-break/) keyword causes the execution jump out of the `switch` statement. If you omit the `break`keyword, the code execution falls through the original `case` into the next one.

If the `expression` does not match any value, the `default_statement` will be executed. It behaves like the `else` block in the `if-else` statement.

The following flowchart illustrates the `switch` statement.

![JavaScript switch case](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-switch-case.png)

You often use a `switch` statement to replace a statement that consists of complicated  `if else`statements chained together. Basically, the  `switch` statement is equivalent to the following  `if else`statement.

| 123456789 | if (expression == value_1) {    statement_1;} else if (expression == value_2) {    statement_2;} else if (expression == value_3) {    statement_3} else {    default_statement;} |
| --------- | ------------------------------------------------------------ |
|           |                                                              |

### JavaScript switch case examples

The following example declares a variable named `day` whose value represents a day in a week. The code outputs the name of the day based on the value of the `day` variable by using the `switch`statement.

| 12345678910111213141516171819202122232425262728 | var day = 3;var dayName;switch (day) {    case 1:        dayName = 'Sunday';        break;    case 2:        dayName = 'Monday';        break;    case 3:        dayName = 'Tuesday';        break;    case 4:        dayName = 'Wednesday';        break;    case 5:        dayName = 'Thursday';        break;    case 6:        dayName = 'Friday';        break;    case 7:        dayName = 'Saturday';        break;    default:        dayName = 'Invalid day';}console.log(dayName); // Tuesday |
| ----------------------------------------------- | ------------------------------------------------------------ |
|                                                 |                                                              |

In this case, `Tuesday` is logged to the web console.

The following script demonstrates how the statements in a `switch` block that fall through. It outputs the number of days in a month based on the input month and year.

| 12345678910111213141516171819202122232425262728293031 | var year = 2016;var month = 2;var dayCount;switch (month) {    case 1:    case 3:    case 5:    case 7:    case 8:    case 10:    case 12:        dayCount = 31;        break;    case 4:    case 6:    case 9:    case 11:        dayCount = 30;        break;    case 2:        if (((year % 4 == 0) && !(year % 100 == 0))            \|\| (year % 400 == 0))            dayCount = 29;        else            dayCount = 28;        break;    default:        dayCount = -1; // invalid month} console.log(dayCount); // 29 |
| ----------------------------------------------------- | ------------------------------------------------------------ |
|                                                       |                                                              |

How it works.

There are four cases in the logic.

- If the month is 1, 3,5, 7, 8, 10, or 12, the number of days in a month is 31.
- If the month 4, 6, 9, or 11, the number of days in that month is 30.
- If the month is 2, and the year is not the leap year, the number of days is 28. If the year is the leap year, the number of  days is 29.
- If the input month is not in the range, the script jumps the default branch and set the dayCount variable to -1 that indicate invalid month.

In this tutorial, you have learned how to use the JavaScript `switch case` statement to control complex conditional branching in the script.

## JavaScript while Loop

**Summary**: in this tutorial, you will learn how to use the JavaScript `while` statement to create a loop.

### Introduction to the JavaScript while loop statement

The JavaScript `while` statement creates a loop that executes a block of code as long as the test condition evaluates to `true`.

The following illustrates the syntax of the `while` statement.

| 123  | while (expression) {    // statement} |
| ---- | ------------------------------------- |
|      |                                       |

The `while` statement evaluates the `expression` before each iteration of the loop. If the `expression`evaluates to `true`, the `while` statement executes the `statement`. If the expression evaluates to `false`, execution continues with the statement after the `while` loop.

The `while` loop evaluates the `expression` before each iteration, therefore, the `while` loop is known as a pretest loop. Because of this, it is possible that the `statement` inside the `while` loop is never executed.

The following flowchart illustrates the `while` loop statement.

![JavaScript while loop](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-while-loop.png)

Note that if you want to execute the statement a least one, and check the condition after each iteration, you should use the [do-while](http://www.javascripttutorial.net/javascript-do-while/) statement.

### JavaScript while loop examples

See the following example that uses the `while` statement.

| 12345 | var count = 1;while (count < 10) {    console.log(count);    count +=2;} |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

How the script works

- First, outside of the loop, the `count` variable is set to 1.
- Second, before the first iteration begins, the `while` statement checks if `count` is less than `10`and execute the statements inside the loop body.
- Third, in each iteration, the loop increments `count` by `2` and after `5` iterations, the condition `count < 10` is no longer `true`, so the loop terminates.

The output of the script in the web console is as follows:

| 12345 | 13579 |
| ----- | ----- |
|       |       |

In this tutorial, you have learned how to use the JavaScript `while` statement to create a pretest loop that executes a block of code as long as the condition is `true`.

## JavaScript do-while Loop

**Summary**: in this tutorial, you will learn how to use the JavaScript `do-while` statement to create a loop.

### Introduction to the JavaScript do-while statement

The `do-while` loop statement creates a loop that executes a block of code until a test condition evaluates to `false`. The following statement illustrates the syntax of the `do-while` loop:

| 123  | do{  statement(s);} while(expression); |
| ---- | -------------------------------------- |
|      |                                        |

Unlike the [`while`](http://www.javascripttutorial.net/javascript-while-loop/) loop, the `do-while` loop always executes the body at least one before it evaluates the expression. Because the expression is evaluated only after the body of the loop has been executed, the `do-while` loop is called post-test loop.

Inside the body of the loop, you need to make changes to some [variable](http://www.javascripttutorial.net/javascript-variables/) to ensure that the expression evaluates to `false` after iterations. Otherwise, you will have an indefinite loop.

Note that from ES6+, the trailing semicolon (;) that follows the `while(expression)` is optional.

The following flowchart illustrates the `do-while` loop statement:

![JavaScript do while loop](http://www.javascripttutorial.net/wp-content/uploads/2016/08/JavaScript-do-while-loop.png)

### JavaScript do-while statement example

See the following example of the `do-while` loop statement.

| 12345 | let count = 0;do {    count++;    console.log('count is:' + count);} while (count < 10); |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

In this example, the `count` variable starts at 0 and is incremented by one each time through the loop. The loop continues as long as the `count` is less than 10.

You often use the `do-while` statement in the situation that body of the loop needs to execute at least one. This is an important feature of the `do-while` loop. The most typical example of using the `do-while` loop is getting an input from the user until the value provided is expected.

Let’s use the `do-while` loop to develop a simple guessing game.

The script generates a random integer between 1 and 12. You have to guess the number by making guesses until the number you choose matches with the number that script chose.

See the following guessing script.

| 1234567891011121314151617181920212223242526 | // generate secret number is a random integer between 1 and 12const MIN = 1;const MAX = 12; var secretNumber = Math.floor(Math.random() * (MAX - MIN + 1)) + MIN; var guesses = 0; // for storing the number of guessesvar hint = ''; // for storing hint do {    // get input from user    var input = prompt(`Please enter a number between ${MIN} and ${MAX}` + hint);    // get the integer    var number = parseInt(input);    // increase the number of guesses    guesses++;    // check input number with the secret number    // provide hint if needed    if (number > secretNumber) {        hint = ', and less than ' + number;    } else if (number < secretNumber) {        hint = ', and greater than ' + number;    } else if(number == secretNumber) {        alert(`Bravo! you're correct after ${guesses} guess(es).`);    }} while (number != secretNumber); |
| ------------------------------------------- | ------------------------------------------------------------ |
|                                             |                                                              |

How it works.

- First, generate a random number between the `MIN` (included) and `MAX` (included) function.
- Second, get a random integer from the user and check it with the secret number. If the number is different from the secret number, give the user a hint, otherwise, display the congratulation message.
- Third, repeat the second step until the number provided by user matches with the generated random number.

In this tutorial, you have learned how to use the `do-while` loop statement to create a post-test loop that allows the body of the loop to execute at least one and to execute until the test condition evaluates to `false`.

## JavaScript for Loop

**Summary**: in this tutorial, you will learn how to use the JavaScript `for` loop statement to create a loop with various options.

### Introduction to the JavaScript for loop statement

The JavaScript `for` loop statement allows you to create a loop with three optional expressions as follows:

| 123  | for (initialization; condition; post-expression) {    // statements} |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

The `initialization` expression initializes the loop. The initialization expression is executed once, as the loop starts. The `initialization` is typically used to initialize a counter variable. If the counter variable is declared using the `var` keyword, the counter variable is not local to the loop. It means that you can reference to the variable after the loop ends. However, if the `let` keyword is used, the counter variable is local to the loop.

The `condition` is an expression evaluated before each loop iteration. The statement inside the loop is executed only when the `condition `expression evaluates to `true`. The loop is terminated if the termination evaluates to `false`. Note that the `condition` is optional. If you omit it, the `for` loop statement considers it as `true`.

The `for` loop statement also evaluates the `post-expression` after each loop iteration. Generally, we use the `post-expression` to update the counter variable.

Three expressions of the `for` loop are optional therefore the following statement creates an indefinite loop:

| 1234 | // infinite loopfor ( ; ; ) {   // statements} |
| ---- | ---------------------------------------------- |
|      |                                                |

### JavaScript for loop examples

The following example uses the `for` statement that declares a variable  `i` and initializes it to 0. It checks that the variable `i` is less than 5, logs the value of  `i`, and increments  `i` by 1 after each loop iteration.

| 1234 | for (var i = 1; i < 5; i++) {    console.log('inside the loop:' + i);}console.log('outside the loop:' + i); // 5; |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Note that because we use the `var` keyword to declare the variable  `i`, the scope of `i` is the same as the scope of the loop, therefore, after the loop, we can access the variable `i`.

From ES6, to declare a variable that is local to the loop, you use the `let` keyword as follows:

| 1234 | for (let j = 1; j < 10; j += 2) {    console.log(j);}console.log(j); // ReferenceError: j is not defined |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

In each iteration, we increment the variable j by 2 and output its value to the web console. After the loop, we reference the variable j and get the `ReferenceError` error.

In the following example, the initialization is omitted.

| 1234 | var j = 1;for (; j < 10; j += 2) {    console.log(j);} |
| ---- | ------------------------------------------------------ |
|      |                                                        |

Similar to the `initialization` expression, the `condition` expression is optional. If you omit the `condition` expression, you need to use a `break` statement to terminate the loop.

| 123456 | for (let j = 1; ; j += 2) {    console.log(j);    if (j < 10) {        break;    }} |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

All three expressions of the `for` loop statement are optional therefore you can omit all of them. Again, you must use a `break` statement to terminate the loop and also modify the counter variable to make the condition for the `break` statement become `true` at some point.

| 123456789 | // initialize j variablevar j = 1;for (; ;) {    // terminate the loop if j is greater than 10;    if (j > 10) break;    console.log(j);    // increase the counter j    j += 2;} |
| --------- | ------------------------------------------------------------ |
|           |                                                              |

Interesting enough, the for statement can have no statement in its loop body. In this case, you place a semicolon (;) immediately after the `for` statement.

The following example calculates the sum of numbers from 1 to 10. The expression is placed at the `post-expression`, therefore, it uses an empty statement in the loop body.

| 1234 | // calculate the sum of the set (1,9)var sum = 0;for (var i = 0; i <= 9; i++, sum += i);console.log(sum); // 55 |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

In this tutorial, you have learned how to use the JavaScript `for` loop statement to create a loop with various options.

## JavaScript break Statement: Control the Execution of Code in a Loop

**Summary**: in this tutorial, you will learn how to use the JavaScript `break` statement to control the execution of code in a loop.

Before discussing the break statement, let’s talk about the label statement first.

### Label statement

In JavaScript, you can label a statement for later use.  The following illustrates the syntax of the label statement.

| 1    | label: statement; |
| ---- | ----------------- |
|      |                   |

The label can by any valid identifier.

The following example labels the loop using the `outer` label.

| 123  | outer: for (var i = 0; i < 5; i++) {    console.log(i);} |
| ---- | -------------------------------------------------------- |
|      |                                                          |

You can reference to the label by using the `break` or `continue` statement.  Typically, you use the label with nested loop such as [`for`](http://www.javascripttutorial.net/javascript-for-loop/), [`do-while`](http://www.javascripttutorial.net/javascript-do-while/), and [`while`](http://www.javascripttutorial.net/javascript-while-loop/) loop.

### JavaScript break statement

The `break` statement gives you a fine-grained control over the execution fo the code in a loop. The `break` statement terminates the loop immediately and passes control over the next statement after the loop.

Here’s an example.

| 123456 | for (var i = 1; i < 10; i++) {    if (i % 3 == 0) {        break;    }}console.log(i); // 3 |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

In this example, the `for` loop increments the variable i from 1 to 10. In the body of the loop, the `if`statement checks if i is evenly divisible by 3. If so, the break statement is executed and the loop is terminated.

The control is passed to the next statement outside the loop that outputs the variable `i` to the web console.

Besides controlling the loop, you also use the `break` statement to terminate a case branch in the `switch` block. [See how to use the break statement in the `switch` block](http://www.javascripttutorial.net/javascript-switch-case/).

#### Using `break` statement to exit nested loop

As mentioned earlier, you use the `break` statement to terminate a label statement and transfer control to the next statement following the terminated statement. The syntax is as follows:

| 1    | break label; |
| ---- | ------------ |
|      |              |

The `break` statement is typically used to exit the nested loop. See the following example.

| 12345678910 | var iterations = 0;top: for (var i = 0; i < 5; i++) {    for (var j = 0; j < 5; j++) {        iterations++;        if (i === 2 && j === 2) {            break top;        }    }}console.log(iterations); // 13 |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

First, the iterations variable is set to zero.

Second, both loops increment the variable i and j from 1 to 5.  In the inner loop, we increment the `iteration` variable and use an `if` statement to check both i and j equal 2. If so, the `break` statement terminates both loops and passes the control over the next statement following the loop.

In this tutorial, you have learned how to use the JavaScript `break` statement to control the code execution of code in a loop and how to exit a nested loop.

## JavaScript continue: Skips the Current Iteration of a Loop

**Summary**: in this tutorial, you will learn how to use the JavaScript `continue` statement to skip the current iteration of a loop.

The `continue` statement skips the current iteration of a loop and goes to the next one. Because of this, the `continue` statement must appear in the body of a loop or you will get an error. Similar to the

Similar to the [`break`](http://www.javascripttutorial.net/javascript-break/) statement, the `continue` statement has two forms: labeled and unlabeled. For more information on the label statement, see [the `break` statement tutorial](http://www.javascripttutorial.net/javascript-break/).

### Using unlabeled JavaScript  `continue` statement

The unlabeled `continue` statement skips the current iteration of a `for,` `do-while`, or `while` loop. The `continue` statement skips the rest of the code to the end of the innermost body of a loop and evaluates the expression that controls the loop.

In a [`for`](http://www.javascripttutorial.net/javascript-for-loop/) loop, the `continue` skips all the statements underneath it and pass the execution of the code to the update expression, in this case, it is `i++`;

| 12345 | for (var i = 0; i < count; i++) {    if (condition)        continue; // Jumps to expression: i++    // more statement here} |
| ----- | ------------------------------------------------------------ |
|       |                                                              |

In a [`while`](http://www.javascripttutorial.net/javascript-while-loop/) or [`do-while`](http://www.javascripttutorial.net/javascript-do-while/) loop, it jumps back to the expression that controls the loop.

| 12345678 | while (expression)  // continue jumps here{    if (condition) {        continue; // Jumps to expression    }    // more statements here    // ...} |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

| 1234567 | do{    if (condition) {        continue; // Jumps to expression    }    // more statements here    // ...}while(expression); // continue jumps here |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

See the following example.

| 12345678910 | var s = 'This is a JavaScript continue statement demo.';var counter = 0;for (var i = 0; i < s.length; i++) {    if (s.charAt(i) != 's') {        continue;    }    //    counter++;}console.log('The number of s found in the string is ' + counter); |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

How the script works.

- First, the `counter` variable is set to zero.
- Second, the `for` loop steps iterate over a string and counts the occurrences of the letter `s`“. If the current character is not an `s`, the `continue` statement skips the rest of the loop and examines the next character in the string. In case the current character is `s`, the script increments the counter variable.
- Third, the `console.log` outputs the number of `s` character found in the string to the web console.

### Using JavaScript continue with a label

The `continue` statement can include an optional label as follows:

| 1    | continue label; |
| ---- | --------------- |
|      |                 |

The `label` can be any valid identifier.

See the following example.

| 12345678910 | // continue with a labelouter: for (var i = 1; i <= 3; i++) {    for (var j = 1; j <= 3; j++) {        if ((i == 2) && (j == 2)) {            console.log('continue to outer');            continue outer;        }        console.log("[i:" + i + ",j:" + j + "]");    }} |
| ----------- | ------------------------------------------------------------ |
|             |                                                              |

How the script works.

- First, the `for` loops increment the variable `i` and `j` from 1 to 3.
- Second, inside the body of the innermost loop, we check if both `i` and `j` are equal to 2. If so, we output a message to the web console and jump back to the `outer` label. Otherwise, we output the values of `i` and `j` in each iteration.

The following shows the result of the script in the web console.

| 12345678 | [i:1,j:1][i:1,j:2][i:1,j:3][i:2,j:1]continue to outer[i:3,j:1][i:3,j:2][i:3,j:3] |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

As you see, when both `i` and `j` are equal to 3, the execution of the code jumps back to the expression `i++` in the outer loop.

In this tutorial, we have been showing you how to use the JavaScript `continue` statement to skip the current iteration of a loop.