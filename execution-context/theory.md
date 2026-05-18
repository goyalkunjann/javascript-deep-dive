# JavaScript Execution Context (Deep Dive)

## What is Execution Context?

Execution Context is the environment in which JavaScript code is executed.

In simple terms:

Execution Context tells JavaScript:

* what code to run
* how to run it
* in what order to run it

Every JavaScript code runs inside an execution context.

---

# Types of Execution Context

## 1. Global Execution Context (GEC)

The default execution context created when JavaScript starts executing.

There is only one Global Execution Context.

Example:

```js
var a = 10;

function test() {
  console.log("Hello");
}
```

The above code runs inside Global Execution Context.

---

## 2. Function Execution Context (FEC)

Whenever a function is invoked, JavaScript creates a new execution context for that function.

Example:

```js
function greet() {
  console.log("Hello");
}

greet();
```

When `greet()` is called, a new Function Execution Context is created.

---

# How JavaScript Executes Code

JavaScript executes code in two phases:

1. Memory Creation Phase
2. Code Execution Phase

---

# 1. Memory Creation Phase

During this phase:

* memory is allocated for variables and functions
* variables are initialized
* function definitions are stored

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

# 2. Code Execution Phase

During this phase:

* code executes line by line
* values are assigned
* functions are invoked

Example:

```js
a = 10
```

---

# Execution Context Creation

Example:

```js
var a = 10;

function test() {
  console.log("Hello");
}

test();
```

---

# Step 1: Global Execution Context Created

JavaScript creates:

* memory space
* thread of execution

---

# Step 2: Memory Creation Phase

Memory:

```js
a -> undefined
test -> function definition
```

---

# Step 3: Code Execution Phase

```js
a = 10
test() executes
```

---

# Thread of Execution

JavaScript executes code one line at a time.

This is called thread of execution.

Example:

```js
console.log("A");
console.log("B");
console.log("C");
```

Output:

```js
A
B
C
```

JavaScript runs code sequentially.

---

# JavaScript is Single Threaded

JavaScript executes one command at a time.

It has:

* one call stack
* one thread of execution

This is why JavaScript is called single-threaded.

---

# Variable Environment

Variables and functions are stored inside the execution context.

Example:

```js
var a = 10;

function test() {}
```

Variable environment:

```js
a -> 10
test -> function
```

---

# Function Invocation

Whenever a function is called:

* a new execution context is created
* function executes
* context gets removed after completion

Example:

```js
function one() {
  two();
}

function two() {
  console.log("Hello");
}

one();
```

Execution order:

* Global Execution Context
* one() context
* two() context

---

# Execution Context Lifecycle

1. Execution Context Created
2. Memory Allocation
3. Code Execution
4. Context Destroyed

---

# Real Internal Visualization

Code:

```js
var a = 10;

function x() {
  console.log("Hello");
}

x();
```

Memory Phase:

```js
a -> undefined
x -> function definition
```

Execution Phase:

```js
a = 10
x() executes
```

---

# Relationship with Hoisting

Hoisting happens because of Memory Creation Phase.

Variables and functions are allocated memory before execution.

---

# Relationship with Call Stack

Every execution context gets pushed into the call stack.

After execution completes:

* execution context is removed from stack

---

# Important Points

* Every JavaScript code runs inside execution context
* JavaScript creates Global Execution Context first
* Functions create their own execution context
* JavaScript runs in two phases
* JavaScript is single-threaded
* Hoisting happens during memory phase

---

# Key Takeaways

* Execution Context is the environment where JS code runs
* JavaScript has Global and Function Execution Context
* Code executes in memory phase and execution phase
* Functions create new execution contexts
* JavaScript executes code line by line
* Execution context is foundation of hoisting and call stack
