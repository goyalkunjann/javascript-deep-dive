# JavaScript Callback Questions

# Theory Questions

## Q1

What is Callback Function?

Answer:

A function passed as argument to another function.

---

## Q2

Why are callbacks used?

Answer:

Callbacks are used for:

* asynchronous operations
* delayed execution
* event handling

---

## Q3

What are First Class Functions?

Answer:

Functions that can:

* be passed
* stored
* returned

---

## Q4

Difference between synchronous and asynchronous callback?

Answer:

| Synchronous Callback | Asynchronous Callback |
| -------------------- | --------------------- |
| Executes immediately | Executes later        |

---

## Q5

What is Callback Hell?

Answer:

Nested callbacks creating unreadable code structure.

---

## Q6

Why is Callback Hell bad?

Answer:

* hard to read
* difficult debugging
* difficult maintenance

---

## Q7

What is Inversion of Control?

Answer:

When we pass callback to another function and lose execution control.

---

## Q8

Why were Promises introduced?

Answer:

Promises solve:

* callback hell
* inversion of control

---

## Q9

Are callbacks synchronous or asynchronous?

Answer:

Callbacks can be both synchronous and asynchronous.

---

## Q10

Give real-world examples of callbacks.

Answer:

* setTimeout
* event listeners
* API calls
* database operations

---

# Practical Coding Questions

## Q11

```js id="cbq1"
function greet(name, callback) {
  console.log("Hello " + name);

  callback();
}

function sayBye() {
  console.log("Bye");
}

greet("Kunjan", sayBye);
```

Output:

```js id="cbq2"
Hello Kunjan
Bye
```

---

## Q12

```js id="cbq3"
function process(callback) {
  callback();
}

process(() => {
  console.log("Executed");
});
```

Output:

```js id="cbq4"
Executed
```

---

## Q13

```js id="cbq5"
console.log("Start");

setTimeout(() => {
  console.log("Callback");
}, 0);

console.log("End");
```

Output:

```js id="cbq6"
Start
End
Callback
```

Why:

Callback waits until call stack becomes empty.

---

## Q14

```js id="cbq7"
setTimeout(() => {
  console.log("Hello");
}, 1000);
```

Output after 1 second:

```js id="cbq8"
Hello
```

---

## Q15

```js id="cbq9"
function calculate(a, b, operation) {
  return operation(a, b);
}

function add(x, y) {
  return x + y;
}

console.log(calculate(2, 3, add));
```

Output:

```js id="cbq10"
5
```

---

## Q16

```js id="cbq11"
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

console.log("C");
```

Output:

```js id="cbq12"
A
C
B
```

---

## Q17

```js id="cbq13"
function fetchData(callback) {
  setTimeout(() => {
    callback("Data Received");
  }, 1000);
}

fetchData((data) => {
  console.log(data);
});
```

Output after 1 second:

```js id="cbq14"
Data Received
```

---

## Q18

```js id="cbq15"
const arr = [1, 2, 3];

arr.forEach(num => {
  console.log(num);
});
```

Output:

```js id="cbq16"
1
2
3
```

Why:

forEach uses callback internally.

---

## Q19

```js id="cbq17"
button.addEventListener("click", () => {
  console.log("Clicked");
});
```

Question:

When does callback execute?

Answer:

When click event occurs.

---

## Q20

```js id="cbq18"
setTimeout(() => {
  console.log("Step 1");

  setTimeout(() => {
    console.log("Step 2");

    setTimeout(() => {
      console.log("Step 3");
    }, 1000);

  }, 1000);

}, 1000);
```

Question:

What problem does this represent?

Answer:

Callback Hell.

---

## Q21

```js id="cbq19"
console.log("Start");

function test(callback) {
  callback();
}

test(() => {
  console.log("Inside Callback");
});

console.log("End");
```

Output:

```js id="cbq20"
Start
Inside Callback
End
```

---

## Q22

```js id="cbq21"
function outer(callback) {
  console.log("Outer");

  callback();
}

outer(() => {
  console.log("Inner");
});
```

Output:

```js id="cbq22"
Outer
Inner
```

---

## Q23

```js id="cbq23"
setTimeout(() => {
  console.log("Timeout");
}, 2000);

console.log("Immediate");
```

Output:

```js id="cbq24"
Immediate
Timeout
```

---

## Q24

```js id="cbq25"
function execute(callback) {
  return callback();
}

console.log(execute(() => "Hello"));
```

Output:

```js id="cbq26"
Hello
```

---

## Q25

```js id="cbq27"
function test(cb) {
  console.log(typeof cb);
}

test(() => {});
```

Output:

```js id="cbq28"
function
```
