# JavaScript Event Loop (Deep Dive)

# What is Event Loop?

Event Loop is a mechanism that allows JavaScript to perform asynchronous operations even though JavaScript is single-threaded.

In simple terms:

Event Loop continuously checks:

* is call stack empty?
* if yes → move tasks from callback queue to call stack

---

# Why Event Loop is Important

* Handles asynchronous operations
* Works with callbacks
* Manages execution order
* Foundation of Promises and Async Await
* Common interview topic

---

# JavaScript is Single Threaded

JavaScript has:

* one call stack
* one thread of execution

It executes one task at a time.

---

# Problem Without Event Loop

If JavaScript waited for every async task:

* browser would freeze
* UI would stop responding

Event Loop solves this problem.

---

# Components of Event Loop System

## 1. Call Stack

Executes synchronous code.

---

## 2. Web APIs

Provided by browser.

Examples:

* setTimeout
* DOM APIs
* fetch
* event listeners

---

## 3. Callback Queue

Stores callbacks waiting for execution.

---

## 4. Event Loop

Checks:

* is call stack empty?

If yes:

* pushes callback into stack.

---

# Basic Example

```js id="evth1"
console.log("Start");

setTimeout(() => {
  console.log("Callback");
}, 0);

console.log("End");
```

Output:

```js id="evth2"
Start
End
Callback
```

---

# How It Works Internally

## Step 1

```js id="evth3"
console.log("Start");
```

Executes immediately.

---

## Step 2

```js id="evth4"
setTimeout(...)
```

Timer goes to Web API.

---

## Step 3

```js id="evth5"
console.log("End");
```

Executes immediately.

---

## Step 4

Timer completes.

Callback moves to Callback Queue.

---

## Step 5

Event Loop checks:

* call stack empty?

YES.

Moves callback into stack.

---

## Step 6

```js id="evth6"
console.log("Callback");
```

Executes.

---

# setTimeout Does NOT Guarantee Exact Timing

```js id="evth7"
setTimeout(() => {
  console.log("Hello");
}, 0);
```

0ms means:

* minimum delay
* callback still waits for call stack to become empty

---

# Callback Queue

Stores async callbacks.

Examples:

* setTimeout callbacks
* event listeners
* async operations

---

# Event Loop Flow

```js id="evth8"
Call Stack → Empty?
↓
YES
↓
Move Callback Queue task into Stack
```

---

# Blocking the Call Stack

```js id="evth9"
console.log("Start");

while (true) {}

console.log("End");
```

Output:

```js id="evth10"
Start
```

Why:

Infinite loop blocks call stack.

---

# Real World Examples

* API calls
* Event listeners
* Timers
* Async operations

---

# Important Points

* JavaScript is single-threaded
* Event Loop handles async tasks
* Web APIs handle timers/events
* Callback Queue stores callbacks
* Event Loop checks call stack continuously

---

# Key Takeaways

* Event Loop enables asynchronous JavaScript
* Call Stack executes synchronous code
* Web APIs handle async operations
* Callback Queue stores completed callbacks
* Event Loop moves callbacks into stack
