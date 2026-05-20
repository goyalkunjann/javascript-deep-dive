# JavaScript Promises Questions

# Theory Questions

## Q1

What is a Promise?

Answer:

A Promise is an object representing future completion or failure of async operation.

---

## Q2

Why were Promises introduced?

Answer:

Promises solve:

* callback hell
* inversion of control

---

## Q3

What are Promise states?

Answer:

| State     | Meaning |
| --------- | ------- |
| Pending   | Initial |
| Fulfilled | Success |
| Rejected  | Failure |

---

## Q4

What does resolve() do?

Answer:

Marks promise as fulfilled.

---

## Q5

What does reject() do?

Answer:

Marks promise as rejected.

---

## Q6

What does .then() do?

Answer:

Handles fulfilled promise.

---

## Q7

What does .catch() do?

Answer:

Handles rejected promise.

---

## Q8

What is Promise Chaining?

Answer:

Using multiple `.then()` methods sequentially.

---

## Q9

Difference between callback and promise?

Answer:

| Callback       | Promise |
| -------------- | ------- |
| Callback Hell  | Cleaner |
| Hard to manage | Easier  |

---

## Q10

Why do Promises execute before setTimeout?

Answer:

Because Promise callbacks use microtask queue.

---

# Practical Coding Questions

## Q11

```js id="prq1"
const promise = new Promise((resolve, reject) => {
  resolve("Success");
});

promise.then(data => {
  console.log(data);
});
```

Output:

```js id="prq2"
Success
```

---

## Q12

```js id="prq3"
const promise = new Promise((resolve, reject) => {
  reject("Error");
});

promise.catch(err => {
  console.log(err);
});
```

Output:

```js id="prq4"
Error
```

---

## Q13

```js id="prq5"
Promise.resolve(10)
  .then(num => num * 2)
  .then(num => console.log(num));
```

Output:

```js id="prq6"
20
```

---

## Q14

```js id="prq7"
console.log("Start");

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

Output:

```js id="prq8"
Start
End
Promise
```

---

## Q15

```js id="prq9"
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

Promise.resolve().then(() => {
  console.log("3");
});

console.log("4");
```

Output:

```js id="prq10"
1
4
3
2
```

---

## Q16

```js id="prq11"
Promise.resolve("Hello")
  .then(data => {
    console.log(data);

    return "World";
  })
  .then(data => {
    console.log(data);
  });
```

Output:

```js id="prq12"
Hello
World
```

---

## Q17

```js id="prq13"
Promise.reject("Failed")
  .catch(err => {
    console.log(err);
  });
```

Output:

```js id="prq14"
Failed
```

---

## Q18

```js id="prq15"
new Promise((resolve) => {
  resolve(5);
})
.then(num => num + 5)
.then(num => num * 2)
.then(num => console.log(num));
```

Output:

```js id="prq16"
20
```

---

## Q19

```js id="prq17"
Promise.all([
  Promise.resolve(1),
  Promise.resolve(2)
]).then(data => {
  console.log(data);
});
```

Output:

```js id="prq18"
[1, 2]
```

---

## Q20

```js id="prq19"
console.log("A");

Promise.resolve().then(() => {
  console.log("B");
});

console.log("C");
```

Output:

```js id="prq20"
A
C
B
```

---

## Q21

```js id="prq21"
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Done");
  }, 1000);
});

promise.then(data => {
  console.log(data);
});
```

Output after 1 second:

```js id="prq22"
Done
```

---

## Q22

```js id="prq23"
Promise.resolve()
  .then(() => {
    return Promise.resolve("Inner Promise");
  })
  .then(data => {
    console.log(data);
  });
```

Output:

```js id="prq24"
Inner Promise
```

---

## Q23

```js id="prq25"
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

Output:

```js id="prq26"
Start
End
Promise
Timeout
```

---

## Q24

```js id="prq27"
Promise.resolve(1)
  .then(num => num + 1)
  .then(num => num + 1)
  .then(num => console.log(num));
```

Output:

```js id="prq28"
3
```

---

## Q25 — GOLDMAN SACHS STYLE

```js id="prq29"
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

Promise.resolve().then(() => {
  console.log("3");
});

Promise.resolve().then(() => {
  console.log("4");
});

console.log("5");
```

Output:

```js id="prq30"
1
5
3
4
2
```
