# JavaScript Closures Questions

# Beginner Questions

## Q1

```js
function outer() {
  let a = 10;

  function inner() {
    console.log(a);
  }

  return inner;
}

outer()();
```

Output:
10

Why:
Inner function remembers variable `a`.

---

## Q2

```js
function test() {
  let count = 0;

  return function () {
    count++;
    console.log(count);
  };
}

const fn = test();

fn();
fn();
```

Output:
1
2

Why:
Closure preserves `count`.

---

## Q3

```js
function x() {
  var a = 7;

  function y() {
    console.log(a);
  }

  return y;
}

const z = x();

z();
```

Output:
7

---

## Q4

```js
function outer() {
  let name = "JavaScript";

  return function () {
    console.log(name);
  };
}

const fn = outer();

fn();
```

Output:
JavaScript

---

## Q5

```js
function counter() {
  let count = 0;

  return function () {
    return ++count;
  };
}

const c = counter();

console.log(c());
console.log(c());
console.log(c());
```

Output:
1
2
3

---

# Intermediate Questions

## Q6

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

Output:
3
3
3

Why:
All callbacks share same variable `i`.

---

## Q7

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

Output:
0
1
2

Why:
`let` creates new variable for each iteration.

---

## Q8

```js
function test() {
  let a = 10;

  return function () {
    console.log(a);
  };
}

const fn1 = test();
const fn2 = test();

fn1();
fn2();
```

Output:
10
10

---

## Q9

```js
function outer() {
  let a = 1;

  return function inner() {
    a++;
    console.log(a);
  };
}

const fn = outer();

fn();
fn();
fn();
```

Output:
2
3
4

---

## Q10

```js
function x() {
  let a = 100;

  return function y() {
    console.log(a);
  };
}

let z = x();

z();
```

Output:
100

---

# Advanced Questions

## Q11

```js
for (var i = 1; i <= 3; i++) {
  (function(i) {
    setTimeout(() => console.log(i), 100);
  })(i);
}
```

Output:
1
2
3

Why:
IIFE creates new scope.

---

## Q12

```js
function outer(b) {
  return function inner() {
    console.log(b);
  };
}

const fn = outer("Closure");

fn();
```

Output:
Closure

---

## Q13

```js
function test() {
  var a = 10;

  return function () {
    console.log(a++);
  };
}

const fn = test();

fn();
fn();
fn();
```

Output:
10
11
12

---

## Q14

```js
function createBankAccount(balance) {
  return {
    deposit(amount) {
      balance += amount;
      console.log(balance);
    }
  };
}

const account = createBankAccount(100);

account.deposit(50);
account.deposit(50);
```

Output:
150
200

---

## Q15

```js
function x() {
  let a = 10;

  return function y() {
    return function z() {
      console.log(a);
    };
  };
}

x()()();
```

Output:
10

---

# Frequently Asked Interview Questions

* What is closure?
* How closures work internally?
* Difference between scope and closure?
* Why are closures important?
* How do closures help in data hiding?
* Why does setTimeout with var print same values?
* How to fix closure issue in loops?
* Real world use cases of closures?
* Can closures cause memory leaks?
* How does React use closures?
