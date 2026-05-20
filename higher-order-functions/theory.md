# JavaScript Higher Order Functions (Deep Dive)

# What are Higher Order Functions?

A Higher Order Function (HOF) is a function that:

* takes another function as argument
  OR
* returns another function

---

# Why Higher Order Functions are Important

* Used heavily in JavaScript
* Important for React
* Used in functional programming
* Used in array methods
* Common interview topic

---

# Functions are First Class Citizens

In JavaScript, functions behave like normal values.

Functions can:

* be stored in variables
* be passed as arguments
* be returned from functions

Example:

```js id="hofth1"
function greet() {
  console.log("Hello");
}

const fn = greet;

fn();
```

Output:

```js id="hofth2"
Hello
```

---

# Callback Function

A function passed as argument to another function is called callback function.

Example:

```js id="hofth3"
function x(callback) {
  callback();
}

x(function () {
  console.log("Callback Executed");
});
```

Output:

```js id="hofth4"
Callback Executed
```

---

# Higher Order Function Example

```js id="hofth5"
function calculate(a, b, operation) {
  return operation(a, b);
}

function add(x, y) {
  return x + y;
}

console.log(calculate(2, 3, add));
```

Output:

```js id="hofth6"
5
```

Why:

`calculate()` takes another function as argument.

---

# Function Returning Function

```js id="hofth7"
function outer() {
  return function inner() {
    console.log("Inner Function");
  };
}

const fn = outer();

fn();
```

Output:

```js id="hofth8"
Inner Function
```

---

# map()

`map()` creates a new array by transforming each element.

Example:

```js id="hofth9"
const arr = [1, 2, 3];

const result = arr.map(num => num * 2);

console.log(result);
```

Output:

```js id="hofth10"
[2, 4, 6]
```

---

# filter()

`filter()` creates a new array containing elements that satisfy condition.

Example:

```js id="hofth11"
const arr = [1, 2, 3, 4];

const result = arr.filter(num => num % 2 === 0);

console.log(result);
```

Output:

```js id="hofth12"
[2, 4]
```

---

# reduce()

`reduce()` reduces array into single value.

Example:

```js id="hofth13"
const arr = [1, 2, 3];

const result = arr.reduce((acc, curr) => acc + curr, 0);

console.log(result);
```

Output:

```js id="hofth14"
6
```

---

# forEach()

`forEach()` executes callback for every element.

Example:

```js id="hofth15"
const arr = [1, 2, 3];

arr.forEach(num => {
  console.log(num);
});
```

Output:

```js id="hofth16"
1
2
3
```

---

# Difference Between map and forEach

| map                     | forEach                   |
| ----------------------- | ------------------------- |
| Returns new array       | Does not return new array |
| Used for transformation | Used for iteration        |

---

# Difference Between filter and map

| filter                  | map                        |
| ----------------------- | -------------------------- |
| Returns filtered values | Returns transformed values |

---

# Difference Between map filter reduce

| Method | Purpose      |
| ------ | ------------ |
| map    | Transform    |
| filter | Filter       |
| reduce | Single value |

---

# Functional Programming Concept

Higher Order Functions are core part of functional programming.

They help:

* write cleaner code
* avoid repetition
* improve readability

---

# Real World Use Cases

## map()

Used in React rendering lists.

---

## filter()

Used for searching/filtering data.

---

## reduce()

Used for totals, sums, grouping data.

---

# Important Points

* Functions are first class citizens
* Functions can be passed and returned
* Callback functions are heavily used
* map filter reduce are Higher Order Functions
* Functional programming uses HOFs extensively

---

# Key Takeaways

* HOF takes or returns function
* Callback is function passed into another function
* map transforms array
* filter filters array
* reduce converts array into single value
* Functions behave like normal values in JavaScript
