# JavaScript Higher Order Functions Questions

# Theory Questions

## Q1

What is Higher Order Function?

Answer:

A function that:

* takes another function as argument
  OR
* returns another function.

---

## Q2

What are First Class Functions?

Answer:

Functions in JavaScript behave like normal values.

They can:

* be stored
* passed
* returned

---

## Q3

What is Callback Function?

Answer:

A function passed as argument to another function.

---

## Q4

Why are Higher Order Functions important?

Answer:

They help:

* reuse code
* write cleaner code
* implement functional programming

---

## Q5

Difference between map and forEach?

Answer:

| map                     | forEach               |
| ----------------------- | --------------------- |
| Returns new array       | Does not return array |
| Used for transformation | Used for iteration    |

---

## Q6

Difference between filter and map?

Answer:

| filter           | map                 |
| ---------------- | ------------------- |
| Filters elements | Transforms elements |

---

## Q7

What does reduce do?

Answer:

`reduce()` converts array into single value.

---

## Q8

Which array methods are Higher Order Functions?

Answer:

* map
* filter
* reduce
* forEach

---

## Q9

Can functions be returned from functions?

Answer:

Yes.

Functions are first class citizens.

---

## Q10

What is Functional Programming?

Answer:

Programming style using pure functions and Higher Order Functions.

---

# Practical Coding Questions

## Q11

```js id="hofq1"
function x(fn) {
  fn();
}

x(function () {
  console.log("Hello");
});
```

Output:

```js id="hofq2"
Hello
```

Why:

Function passed as argument acts as callback.

---

## Q12

```js id="hofq3"
function greet(name) {
  return function () {
    console.log("Hello " + name);
  };
}

const fn = greet("Kunjan");

fn();
```

Output:

```js id="hofq4"
Hello Kunjan
```

---

## Q13

```js id="hofq5"
const arr = [1, 2, 3];

const result = arr.map(num => num * 2);

console.log(result);
```

Output:

```js id="hofq6"
[2, 4, 6]
```

---

## Q14

```js id="hofq7"
const arr = [1, 2, 3, 4];

const result = arr.filter(num => num % 2 === 0);

console.log(result);
```

Output:

```js id="hofq8"
[2, 4]
```

---

## Q15

```js id="hofq9"
const arr = [1, 2, 3];

const result = arr.reduce((acc, curr) => acc + curr, 0);

console.log(result);
```

Output:

```js id="hofq10"
6
```

---

## Q16

```js id="hofq11"
const arr = [1, 2, 3];

arr.forEach(num => {
  console.log(num);
});
```

Output:

```js id="hofq12"
1
2
3
```

---

## Q17

```js id="hofq13"
const arr = [1, 2, 3];

const result = arr.map(num => num + 1);

console.log(result);
```

Output:

```js id="hofq14"
[2, 3, 4]
```

---

## Q18

```js id="hofq15"
const arr = [10, 20, 30];

const result = arr.filter(num => num > 15);

console.log(result);
```

Output:

```js id="hofq16"
[20, 30]
```

---

## Q19

```js id="hofq17"
const arr = [1, 2, 3, 4];

const result = arr.reduce((acc, curr) => acc * curr, 1);

console.log(result);
```

Output:

```js id="hofq18"
24
```

---

## Q20

```js id="hofq19"
function calculate(a, b, operation) {
  return operation(a, b);
}

function multiply(x, y) {
  return x * y;
}

console.log(calculate(2, 3, multiply));
```

Output:

```js id="hofq20"
6
```

---

## Q21

```js id="hofq21"
const arr = [1, 2, 3];

const result = arr.map(num => {
  return num * num;
});

console.log(result);
```

Output:

```js id="hofq22"
[1, 4, 9]
```

---

## Q22

```js id="hofq23"
const arr = ["apple", "banana", "kiwi"];

const result = arr.filter(word => word.length > 5);

console.log(result);
```

Output:

```js id="hofq24"
["banana"]
```

---

## Q23

```js id="hofq25"
const arr = [5, 10, 15];

const result = arr.reduce((acc, curr) => acc + curr, 0);

console.log(result);
```

Output:

```js id="hofq26"
30
```

---

## Q24

```js id="hofq27"
function outer() {
  return function inner() {
    console.log("Inner");
  };
}

const fn = outer();

fn();
```

Output:

```js id="hofq28"
Inner
```

---

## Q25

```js id="hofq29"
const arr = [1, 2, 3];

const result = arr.map(num => num.toString());

console.log(result);
```

Output:

```js id="hofq30"
["1", "2", "3"]
```
