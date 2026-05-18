# JavaScript Hoisting Questions

# Beginner Questions

## Q1

```js
console.log(a);

var a = 10;
```

Output:

```js
undefined
```

---

## Q2

```js
console.log(a);

let a = 10;
```

Output:

```js
ReferenceError
```

---

## Q3

```js
console.log(a);

const a = 10;
```

Output:

```js
ReferenceError
```

---

## Q4

```js
var a = 10;

console.log(a);
```

Output:

```js
10
```

---

## Q5

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

---

## Q6

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

---

## Q7

```js
console.log(a);

var a;
```

Output:

```js
undefined
```

---

## Q8

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

---

# Intermediate Questions

## Q9

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

---

## Q10

```js
function test() {
  console.log(a);

  let a = 20;
}

test();
```

Output:

```js
ReferenceError
```

---

## Q11

```js
function test() {
  console.log(a);

  const a = 20;
}

test();
```

Output:

```js
ReferenceError
```

---

## Q12

```js
console.log(a);

function a() {}
```

Output:

```js
function a() {}
```

---

## Q13

```js
console.log(a);

var a = 10;

function a() {}
```

Output:

```js
function a() {}
```

---

## Q14

```js
var a = 10;

function test() {
  console.log(a);
}

test();
```

Output:

```js
10
```

---

## Q15

```js
var a = 10;

function test() {
  var a = 20;

  console.log(a);
}

test();
```

Output:

```js
20
```

---

# Advanced Questions

## Q16

```js
console.log(test);

var test = 10;
```

Output:

```js
undefined
```

---

## Q17

```js
console.log(typeof a);

var a = 10;
```

Output:

```js
undefined
```

---

## Q18

```js
console.log(typeof a);

let a = 10;
```

Output:

```js
ReferenceError
```

---

## Q19

```js
function outer() {
  console.log(a);

  var a = 100;

  function inner() {
    console.log(a);
  }

  inner();
}

outer();
```

Output:

```js
undefined
100
```

---

## Q20

```js
test();

function test() {
  console.log("Function Declaration");
}

var test = function () {
  console.log("Function Expression");
};
```

Output:

```js
Function Declaration
```

---

## Q21

```js
var x = 1;

function x() {
  console.log("Hello");
}

console.log(x);
```

Output:

```js
1
```

---

## Q22

```js
console.log(x);

function x() {}

var x = 20;
```

Output:

```js
function x() {}
```

---

## Q23

```js
function test() {
  console.log(a);

  if (true) {
    var a = 10;
  }
}

test();
```

Output:

```js
undefined
```

---

## Q24

```js
function test() {
  console.log(a);

  if (true) {
    let a = 10;
  }
}

test();
```

Output:

```js
ReferenceError
```

---

## Q25

```js
var a = 1;

function test() {
  console.log(a);

  a = 10;

  console.log(a);

  var a = 100;
}

test();
```

Output:

```js
undefined
10
```

---

# Frequently Asked Interview Questions

* What is hoisting?
* Why does var print undefined?
* Are let and const hoisted?
* What is TDZ?
* Difference between undefined and ReferenceError?
* Difference between function declaration and function expression?
* Why are functions fully hoisted?
* What happens during memory creation phase?
* What is execution phase?
* Difference between TypeError and ReferenceError?
