# JavaScript Hoisting (Deep Dive)

## What is Hoisting?

Hoisting is JavaScript's default behavior of moving declarations to the top before code execution.

In simple terms:

Variables and functions are processed before the code runs.

---

# Important Point

Only declarations are hoisted, not initializations.

---

# Basic Example

```js
console.log(a);

var a = 10;
```

Output:

```js
undefined
```

Why:

JavaScript internally treats the code like this:

```js
var a;

console.log(a);

a = 10;
```

`var a` is hoisted and initialized with `undefined`.

---

# Why Hoisting Happens

Hoisting happens because JavaScript runs in two phases:

1. Memory Creation Phase
2. Code Execution Phase

---

# Memory Creation Phase

JavaScript allocates memory for variables and functions.

Example:

```js
var a = 10;

function test() {}
```

Memory phase:

```js
a -> undefined
test -> full function definition
```

---

# Execution Phase

Code executes line by line.

```js
a = 10
```

---

# var Hoisting

```js
console.log(a);

var a = 10;
```

Output:

```js
undefined
```

Why:

`var` is hoisted and initialized with `undefined`.

---

# let Hoisting

```js
console.log(a);

let a = 10;
```

Output:

```js
ReferenceError
```

Why:

`let` is hoisted but remains inside Temporal Dead Zone (TDZ).

---

# const Hoisting

```js
console.log(a);

const a = 10;
```

Output:

```js
ReferenceError
```

Why:

`const` is also hoisted but remains inside TDZ.

---

# Temporal Dead Zone (TDZ)

TDZ is the time between hoisting and initialization.

During this period variables cannot be accessed.

Example:

```js
console.log(a);

let a = 10;
```

`a` exists in memory but cannot be accessed before initialization.

---

# var vs let vs const (Hoisting Perspective)

| Keyword | Hoisted | Initial Value | Access Before Initialization |
| ------- | ------- | ------------- | ---------------------------- |
| var     | Yes     | undefined     | Allowed                      |
| let     | Yes     | uninitialized | ReferenceError               |
| const   | Yes     | uninitialized | ReferenceError               |

---

# Function Hoisting

Function declarations are fully hoisted.

```js
test();

function test() {
  console.log("Hello");
}
```

Output:

```js
Hello
```

Why:

Entire function definition is hoisted.

---

# Function Expression Hoisting

```js
test();

var test = function () {
  console.log("Hello");
};
```

Output:

```js
TypeError
```

Why:

`test` is hoisted as `undefined`.

Internally:

```js
var test;

test();
```

`undefined()` causes TypeError.

---

# Arrow Function Hoisting

```js
test();

const test = () => {
  console.log("Hello");
};
```

Output:

```js
ReferenceError
```

Why:

`const` stays inside TDZ.

---

# Hoisting with Functions and Variables

```js
console.log(a);

var a = 10;

function a() {}
```

Output:

```js
function a() {}
```

Why:

Function declarations get higher priority during hoisting.

---

# Hoisting Inside Functions

```js
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

Why:

Local variable `a` is hoisted inside the function.

---

# Hoisting and Scope

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

Why:

Local `a` shadows global `a`.

---

# undefined vs ReferenceError vs TypeError

## undefined

Variable exists but value not assigned.

```js
console.log(a);

var a = 10;
```

---

## ReferenceError

Variable accessed before initialization.

```js
console.log(a);

let a = 10;
```

---

## TypeError

Trying to call undefined as function.

```js
test();

var test = function () {};
```

---

# Real Internal Visualization

Code:

```js
var a = 10;

function x() {
  console.log("Hello");
}
```

Memory Phase:

```js
a -> undefined
x -> function definition
```

Execution Phase:

```js
a = 10
```

---

# Frequently Asked Interview Questions

## Q1

What is hoisting in JavaScript?

---

## Q2

Why does var print undefined?

---

## Q3

Are let and const hoisted?

---

## Q4

What is Temporal Dead Zone?

---

## Q5

Difference between undefined and ReferenceError?

---

## Q6

Difference between function declaration and function expression hoisting?

---

## Q7

Why are function declarations fully hoisted?

---

## Q8

Why does function expression give TypeError?

---

## Q9

What happens during memory creation phase?

---

## Q10

How does JavaScript execute code internally?

---

# Key Takeaways

* Hoisting happens during memory creation phase
* var is initialized with undefined
* let and const stay inside TDZ
* Function declarations are fully hoisted
* Function expressions behave like variables
* JavaScript executes code in two phases
