# JavaScript Execution Context Questions with Answers

# Theory Questions

## Q1

What is Execution Context in JavaScript?

Answer:

Execution Context is the environment where JavaScript code is executed.

It contains:

* variables
* functions
* scope information
* this keyword value

Every JavaScript code runs inside an execution context.

---

## Q2

What are the types of Execution Context?

Answer:

1. Global Execution Context (GEC)
2. Function Execution Context (FEC)

---

## Q3

What is Global Execution Context?

Answer:

The default execution context created when JavaScript starts running.

There is only one Global Execution Context in a program.

---

## Q4

What is Function Execution Context?

Answer:

Whenever a function is invoked, JavaScript creates a new execution context for that function.

---

## Q5

What happens during Memory Creation Phase?

Answer:

During memory phase:

* memory is allocated to variables
* var variables initialized with undefined
* function declarations stored completely

Example:

```js
a -> undefined
test -> function definition
```

---

## Q6

What happens during Code Execution Phase?

Answer:

During execution phase:

* code runs line by line
* values assigned
* functions invoked

---

## Q7

Why is JavaScript single-threaded?

Answer:

JavaScript executes one command at a time using:

* one call stack
* one thread of execution

---

## Q8

What is Thread of Execution?

Answer:

JavaScript executes code line by line sequentially.

This flow is called thread of execution.

---

## Q9

How does JavaScript execute code internally?

Answer:

JavaScript executes code in two phases:

1. Memory Creation Phase
2. Code Execution Phase

---

## Q10

How is hoisting related to execution context?

Answer:

Hoisting happens during Memory Creation Phase when variables and functions get memory allocation before execution.

---

## Q11

What is Variable Environment?

Answer:

Variable Environment stores variables and function declarations inside execution context.

---

## Q12

What happens when a function is invoked?

Answer:

When a function is called:

* new Function Execution Context is created
* pushed into call stack
* executed
* removed after completion

---

## Q13

How are execution contexts removed?

Answer:

After execution completes, execution context is popped out from call stack.

---

## Q14

Difference between Global and Function Execution Context?

| Global Execution Context  | Function Execution Context      |
| ------------------------- | ------------------------------- |
| Created once              | Created on every function call  |
| Exists throughout program | Exists until function completes |
| Default context           | Function-specific context       |

---

## Q15

How does execution context relate to call stack?

Answer:

Every execution context gets pushed into the call stack.

After execution finishes:

* it gets removed from stack.

---

# Practical Coding Questions

## Q16

```js
var a = 10;

function test() {
  console.log("Hello");
}

test();
```

Answer:

Memory Phase:

```js
a -> undefined
test -> function definition
```

Execution Phase:

```js
a = 10
test() executes
```

Output:

```js
Hello
```

---

## Q17

```js
console.log(a);

var a = 10;
```

Output:

```js
undefined
```

Answer:

During memory phase:

```js
a -> undefined
```

So console.log(a) prints undefined.

---

## Q18

```js
console.log(a);

let a = 10;
```

Output:

```js
ReferenceError
```

Answer:

`let` is hoisted but remains inside TDZ until initialization.

---

## Q19

```js
function one() {
  console.log("One");
}

function two() {
  console.log("Two");
}

one();
two();
```

Output:

```js
One
Two
```

Answer:

Execution flow:

* Global Execution Context created
* one() called
* one() context created
* one() removed
* two() called
* two() context created
* two() removed

---

## Q20

```js
function one() {
  two();
}

function two() {
  console.log("Hello");
}

one();
```

Output:

```js
Hello
```

Answer:

Execution contexts created:

1. Global Execution Context
2. one() Execution Context
3. two() Execution Context

---

## Q21

```js
var a = 1;

function test() {
  var b = 2;

  console.log(a, b);
}

test();
```

Output:

```js
1 2
```

Answer:

Memory Phase:

```js
a -> undefined
test -> function definition
```

Inside test():

```js
b -> undefined
```

Execution:

```js
a = 1
b = 2
```

---

## Q22

```js
var x = 10;

function outer() {
  var y = 20;

  function inner() {
    console.log(x, y);
  }

  inner();
}

outer();
```

Output:

```js
10 20
```

Answer:

Execution flow:

* Global Execution Context
* outer() context
* inner() context

Variable lookup:

* x found in global scope
* y found in outer scope

---

## Q23

```js
function greet(name) {
  console.log("Hello " + name);
}

greet("JavaScript");
```

Output:

```js
Hello JavaScript
```

Answer:

When greet() is invoked:

* Function Execution Context created
* parameter `name` initialized
* function executes

---

## Q24

```js
var a = 100;

function x() {
  console.log(a);
}

x();
```

Output:

```js
100
```

Answer:

JavaScript searches:

* current scope
* outer scope

`a` found in global scope.

---

## Q25

```js
function first() {
  console.log("First");
  second();
}

function second() {
  console.log("Second");
}

first();
```

Output:

```js
First
Second
```

Answer:

Execution order:

1. Global Execution Context
2. first() context
3. second() context

---

## Q26

```js
var a = 10;

function test() {
  console.log(a);

  var a = 20;
}

test();
```

Output:

```js
undefined
```

Answer:

Inside test():

```js
var a
```

gets hoisted locally.

Memory:

```js
a -> undefined
```

Local variable shadows global variable.

---

## Q27

```js
function one() {
  console.log("One");
}

one();

console.log("Done");
```

Output:

```js
One
Done
```

Answer:

JavaScript executes line by line sequentially using single thread of execution.

---

## Q28

```js
function outer() {
  function inner() {
    console.log("Inner");
  }

  inner();
}

outer();
```

Output:

```js
Inner
```

Answer:

Execution contexts created:

1. Global Execution Context
2. outer() Execution Context
3. inner() Execution Context

---

## Q29

```js
var a = 10;

function x() {
  function y() {
    console.log(a);
  }

  y();
}

x();
```

Output:

```js
10
```

Answer:

Execution flow:

* Global Context
* x() Context
* y() Context

Variable lookup:

* y() checks current scope
* not found
* checks outer/global scope
* finds a = 10

---

## Q30

```js
console.log("Start");

function test() {
  console.log("Inside Test");
}

test();

console.log("End");
```

Output:

```js
Start
Inside Test
End
```

Answer:

Execution order:

1. Start
2. test() invoked
3. Inside Test
4. End
