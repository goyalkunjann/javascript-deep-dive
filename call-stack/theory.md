# JavaScript Call Stack (Deep Dive)

## What is Call Stack?

Call Stack is a mechanism used by JavaScript to keep track of function calls.

In simple terms:

Call Stack stores execution contexts and manages function execution order.

---

# Why Call Stack is Important

* Keeps track of function calls
* Manages execution order
* Handles execution contexts
* Helps JavaScript execute code line by line
* Important for debugging stack overflow errors

---

# JavaScript is Single Threaded

JavaScript executes one command at a time.

It has:

* one call stack
* one thread of execution

This is why JavaScript is called single-threaded.

---

# Call Stack Works on LIFO

LIFO means:

```js id="bq9kxe"
Last In First Out
```

The function added last is removed first.

---

# Basic Example

```js id="sg5b5y"
function one() {
  console.log("One");
}

function two() {
  console.log("Two");
}

one();
two();
```

Execution Flow:

```js id="dh5nfx"
Global()
↓
one()
↓
POP one()
↓
two()
↓
POP two()
↓
POP Global()
```

Output:

```js id="q4e65v"
One
Two
```

---

# How Call Stack Works

Whenever JavaScript starts:

* Global Execution Context is pushed into stack

Whenever a function is called:

* new Function Execution Context is pushed

After function completes:

* execution context is popped out

---

# Push and Pop Operations

## Push

Adding execution context into stack.

Example:

```js id="s3ow5z"
test();
```

`test()` execution context pushed into stack.

---

## Pop

Removing execution context after completion.

---

# Stack Frame

Each execution context inside call stack is called a stack frame.

Example:

```js id="3cbdjl"
Global()
test()
demo()
```

Each one is a stack frame.

---

# Function Invocation Example

```js id="9rsljl"
function one() {
  two();
}

function two() {
  three();
}

function three() {
  console.log("Hello");
}

one();
```

Call Stack Flow:

```js id="8sfr8x"
Global()
↓
one()
↓
two()
↓
three()
↓
POP three()
↓
POP two()
↓
POP one()
↓
POP Global()
```

Output:

```js id="4fj5ig"
Hello
```

---

# Call Stack and Execution Context

Call Stack stores Execution Contexts.

Example:

```js id="b3w5s5"
function test() {
  console.log("Hello");
}

test();
```

Execution Contexts:

* Global Execution Context
* test() Execution Context

---

# Stack Overflow

When too many function calls happen continuously,
stack memory becomes full.

This causes:

```js id="f4v0a8"
Maximum call stack size exceeded
```

---

# Recursive Function Example

```js id="2c5d9k"
function test() {
  test();
}

test();
```

Output:

```js id="uwgh8j"
RangeError: Maximum call stack size exceeded
```

Why:

Function keeps calling itself infinitely.

---

# Real Internal Visualization

Code:

```js id="20wq65"
function one() {
  two();
}

function two() {
  console.log("Two");
}

one();
```

Stack Flow:

```js id="wtx4qa"
1. Global()
2. one()
3. two()
4. POP two()
5. POP one()
6. POP Global()
```

---

# Call Stack and Thread of Execution

JavaScript executes one operation at a time using:

* one thread
* one call stack

This makes JavaScript synchronous by default.

---

# Relationship with Event Loop

The Event Loop continuously checks:

* Is call stack empty?

If yes:

* tasks from callback queue are pushed into stack.

---

# Important Points

* Call Stack manages execution contexts
* JavaScript uses LIFO principle
* Functions are pushed and popped from stack
* Stack overflow happens due to infinite recursion
* JavaScript is single-threaded
* Call Stack works with Event Loop

---

# Key Takeaways

* Call Stack stores execution contexts
* JavaScript uses one call stack
* Functions execute using push and pop
* Last function added executes first
* Infinite recursion causes stack overflow
* Call Stack is core part of JavaScript engine
