# JavaScript call apply bind Questions

# Theory Questions

## Q1

What are call apply bind in JavaScript?

Answer:

They are methods used to manually control the value of `this`.

---

## Q2

What does call() do?

Answer:

`call()` invokes a function immediately and allows setting `this`.

---

## Q3

What does apply() do?

Answer:

`apply()` invokes a function immediately and accepts arguments as array.

---

## Q4

What does bind() do?

Answer:

`bind()` returns a new function with bound `this`.

---

## Q5

Difference between call apply bind?

Answer:

| Method | Executes Immediately | Arguments |
| ------ | -------------------- | --------- |
| call   | Yes                  | Separate  |
| apply  | Yes                  | Array     |
| bind   | No                   | Separate  |

---

## Q6

What is function borrowing?

Answer:

Using methods of one object with another object using call/apply/bind.

---

## Q7

Why is bind useful?

Answer:

It permanently binds `this` to a function.

---

## Q8

Which method returns a new function?

Answer:

`bind()`

---

## Q9

Which method accepts array arguments?

Answer:

`apply()`

---

## Q10

How does call apply bind relate to this keyword?

Answer:

They manually set the value of `this`.

---

# Practical Coding Questions

## Q11

```js id="l2x7n4"
const user = {
  name: "Kunjan"
};

function greet() {
  console.log(this.name);
}

greet.call(user);
```

Output:

```js id="o8v3m1"
Kunjan
```

---

## Q12

```js id="x5t9k7"
const person = {
  name: "Frontend"
};

function intro(city) {
  console.log(this.name + " from " + city);
}

intro.call(person, "Delhi");
```

Output:

```js id="c4y6r2"
Frontend from Delhi
```

---

## Q13

```js id="m1q8w5"
const person = {
  name: "React"
};

function intro(city, country) {
  console.log(this.name + " from " + city + ", " + country);
}

intro.apply(person, ["Noida", "India"]);
```

Output:

```js id="j7k3v9"
React from Noida, India
```

---

## Q14

```js id="b9x4z1"
const user = {
  name: "JavaScript"
};

function show() {
  console.log(this.name);
}

const fn = show.bind(user);

fn();
```

Output:

```js id="g2m6t8"
JavaScript
```

---

## Q15

```js id="p8r1c5"
const user1 = {
  name: "Kunjan"
};

const user2 = {
  name: "Frontend"
};

function greet() {
  console.log(this.name);
}

greet.call(user1);
greet.call(user2);
```

Output:

```js id="d5v9y7"
Kunjan
Frontend
```

---

## Q16

```js id="t4k7m2"
function test(a, b) {
  console.log(a + b);
}

test.call(null, 10, 20);
```

Output:

```js id="v8n3x6"
30
```

---

## Q17

```js id="r6z2w9"
function test(a, b) {
  console.log(a * b);
}

test.apply(null, [10, 20]);
```

Output:

```js id="h1q5p8"
200
```

---

## Q18

```js id="n3v7r1"
const obj = {
  name: "JS"
};

function show() {
  console.log(this.name);
}

const bound = show.bind(obj);

bound();
```

Output:

```js id="u6m2c4"
JS
```

---

## Q19

```js id="y5x8k3"
const person = {
  firstName: "Kunjan",
  lastName: "Goyal"
};

function fullName() {
  console.log(this.firstName + " " + this.lastName);
}

fullName.call(person);
```

Output:

```js id="f7v1d6"
Kunjan Goyal
```

---

## Q20

```js id="c2n9m5"
const person = {
  name: "Frontend"
};

function greet(message) {
  console.log(message + " " + this.name);
}

const fn = greet.bind(person, "Hello");

fn();
```

Output:

```js id="q4x8t1"
Hello Frontend
```

---

## Q21

```js id="w7m3r9"
const obj = {
  value: 100
};

function printValue() {
  console.log(this.value);
}

const fn = printValue;

fn();
```

Output:

```js id="z1c5k7"
undefined
```

Why:

Function lost object reference.

---

## Q22

```js id="s8x2v4"
const obj = {
  value: 100
};

function printValue() {
  console.log(this.value);
}

const fn = printValue.bind(obj);

fn();
```

Output:

```js id="m5q9t2"
100
```

---

## Q23

```js id="a4r7v1"
function greet() {
  console.log(this.name);
}

const user = {
  name: "React"
};

greet.apply(user);
```

Output:

```js id="n8x3k6"
React
```

---

## Q24

```js id="d6m2w8"
const obj1 = {
  name: "A"
};

const obj2 = {
  name: "B"
};

function show() {
  console.log(this.name);
}

const boundFn = show.bind(obj1);

boundFn.call(obj2);
```

Output:

```js id="u9v4r7"
A
```

Why:

bind permanently binds `this`.

---

## Q25

```js id="e3k7n1"
const person = {
  name: "JavaScript"
};

function sayHi() {
  return "Hi " + this.name;
}

console.log(sayHi.call(person));
```

Output:

```js id="g8x2m5"
Hi JavaScript
```
