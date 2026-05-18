# JavaScript Closures (Deep Dive)

## What is Closure?

A closure is created when a function remembers variables from its outer scope even after the outer function has finished execution.

In simple terms:

A closure allows an inner function to access variables of its outer function even after the outer function is completed.

---

# Basic Example

```js
function outer() {
  let a = 10;

  function inner() {
    console.log(a);
  }

  return inner;
}

const fn = outer();

fn();
```

Output:

```js
10
```

Why:

The inner function remembers variable `a` from the outer function.

---

# Why Closures are Important

* Preserves data in memory
* Enables data hiding
* Used in callbacks
* Used in event listeners
* Used heavily in React
* Foundation for debounce/throttle
* Helps create private variables

---

# Closure = Function + Lexical Environment

```js
function outer() {
  let count = 0;

  return function inner() {
    count++;
    console.log(count);
  };
}

const counter = outer();

counter();
counter();
counter();
```

Output:

```js
1
2
3
```

Why:

The inner function remembers `count` even after `outer()` finishes execution.

---

# Lexical Scope and Closures

Closures work because of lexical scoping.

Functions remember where they are created, not where they are called.

```js
let a = 10;

function outer() {
  let b = 20;

  function inner() {
    console.log(a, b);
  }

  return inner;
}

outer()();
```

Output:

```js
10 20
```

---

# Data Hiding using Closures

Closures can create private variables.

```js
function bankAccount() {
  let balance = 1000;

  return {
    deposit(amount) {
      balance += amount;
      console.log(balance);
    },

    getBalance() {
      console.log(balance);
    }
  };
}

const account = bankAccount();

account.deposit(500);
account.getBalance();
```

Output:

```js
1500
1500
```

Why:

`balance` cannot be accessed directly from outside.

---

# Closures in Loops

## Using var

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

Output:

```js
3
3
3
```

Why:

`var` is function scoped and all callbacks share the same variable.

---

## Using let

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

Output:

```js
0
1
2
```

Why:

`let` creates a new variable for every iteration.

---

# Closures with IIFE

```js
for (var i = 0; i < 3; i++) {
  (function(i) {
    setTimeout(() => console.log(i), 100);
  })(i);
}
```

Output:

```js
0
1
2
```

Why:

IIFE creates a new scope for each iteration.

---

# Real World Use Cases of Closures

## 1. Counter

```js
function counter() {
  let count = 0;

  return function () {
    return ++count;
  };
}
```

---

## 2. Event Listeners

```js
button.addEventListener("click", function () {
  console.log("Clicked");
});
```

---

## 3. React Hooks

React hooks internally use closures.

Examples:

* useState
* useEffect

---

## 4. Callbacks

```js
setTimeout(() => {
  console.log("Hello");
}, 1000);
```

---

## 5. Memoization

Closures help store cached values.

---

# Advantages of Closures

* Data privacy
* State preservation
* Encapsulation
* Better control over variables
* Used in asynchronous JavaScript

---

# Disadvantages of Closures

* Increased memory usage
* Can cause memory leaks if not handled properly

---

# Closure vs Scope

| Scope                       | Closure                          |
| --------------------------- | -------------------------------- |
| Defines accessibility       | Remembers variables              |
| Static concept              | Runtime behavior                 |
| Created during code writing | Created during function creation |

---

# Frequently Asked Interview Questions

## Q1

What is closure in JavaScript?

---

## Q2

How do closures work internally?

---

## Q3

Why are closures important?

---

## Q4

Difference between scope and closure?

---

## Q5

How do closures provide data hiding?

---

## Q6

Why does setTimeout with var print same values?

---

## Q7

How to fix closures in loops?

---

## Q8

Can closures cause memory leaks?

---

## Q9

What are real-world use cases of closures?

---

## Q10

How does React use closures?

---

# Key Takeaways

* Closures allow functions to remember outer variables
* Closures depend on lexical scope
* Variables remain alive in memory
* Used heavily in asynchronous JavaScript
* Foundation of advanced JavaScript concepts
