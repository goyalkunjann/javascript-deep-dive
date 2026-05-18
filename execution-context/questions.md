# JavaScript Execution Context Questions

# Theory Questions

## Q1

What is Execution Context in JavaScript?

---

## Q2

What are the types of Execution Context?

---

## Q3

What is Global Execution Context?

---

## Q4

What is Function Execution Context?

---

## Q5

What happens during Memory Creation Phase?

---

## Q6

What happens during Code Execution Phase?

---

## Q7

Why is JavaScript single-threaded?

---

## Q8

What is Thread of Execution?

---

## Q9

How does JavaScript execute code internally?

---

## Q10

How is hoisting related to execution context?

---

## Q11

What is Variable Environment?

---

## Q12

What happens when a function is invoked?

---

## Q13

How are execution contexts removed?

---

## Q14

Difference between Global and Function Execution Context?

---

## Q15

How does execution context relate to call stack?

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

Explain:

* Memory Phase
* Execution Phase

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

Explain using Execution Context.

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

Explain using Memory Phase and TDZ.

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

Explain execution flow.

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

Explain execution contexts created.

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

Explain memory allocation.

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

Explain execution contexts step by step.

---

## Q23

```js
function greet(name) {
  console.log("Hello " + name);
}

greet("JavaScript");
```

Explain function execution context creation.

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

Explain variable lookup.

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

Explain execution order.

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

Explain using execution context.

---

## Q27

```js
function one() {
  console.log("One");
}

one();

console.log("Done");
```

Explain thread of execution.

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

Explain all execution contexts created.

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

Explain execution flow and scope lookup.

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

Explain execution order.
