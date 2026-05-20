# JavaScript Promises (Deep Dive)

# What is a Promise?

A Promise is an object representing the eventual completion or failure of an asynchronous operation.

In simple terms:

Promise handles future values.

---

# Why Promises are Important

Promises solve:

* callback hell
* inversion of control

They make async code cleaner and more readable.

---

# Promise States

A Promise has 3 states:

| State     | Meaning              |
| --------- | -------------------- |
| Pending   | Initial state        |
| Fulfilled | Operation successful |
| Rejected  | Operation failed     |

---

# Creating a Promise

```js id="prth1"
const promise = new Promise((resolve, reject) => {
  resolve("Success");
});
```

---

# Promise Example

```js id="prth2"
const promise = new Promise((resolve, reject) => {
  resolve("Data Received");
});

promise.then((data) => {
  console.log(data);
});
```

Output:

```js id="prth3"
Data Received
```

---

# resolve()

`resolve()` marks promise as fulfilled.

Example:

```js id="prth4"
resolve("Success");
```

---

# reject()

`reject()` marks promise as failed.

Example:

```js id="prth5"
reject("Error");
```

---

# .then()

Used to handle fulfilled promises.

Example:

```js id="prth6"
promise.then((data) => {
  console.log(data);
});
```

---

# .catch()

Used to handle rejected promises.

Example:

```js id="prth7"
promise.catch((error) => {
  console.log(error);
});
```

---

# Promise Rejection Example

```js id="prth8"
const promise = new Promise((resolve, reject) => {
  reject("Something went wrong");
});

promise.catch((error) => {
  console.log(error);
});
```

Output:

```js id="prth9"
Something went wrong
```

---

# Promise Chaining

```js id="prth10"
Promise.resolve(1)
  .then(num => num + 1)
  .then(num => num + 1)
  .then(num => console.log(num));
```

Output:

```js id="prth11"
3
```

---

# Why Promise Chaining is Important

It avoids callback hell.

---

# Promise vs Callback

| Callback       | Promise               |
| -------------- | --------------------- |
| Callback Hell  | Cleaner chaining      |
| Hard to manage | Easier async handling |

---

# Promise Microtask Queue

Promise callbacks go into:

* Microtask Queue

Microtasks execute before callback queue tasks.

---

# Example

```js id="prth12"
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

```js id="prth13"
Start
End
Promise
Timeout
```

Why:

Promise microtasks execute before setTimeout callbacks.

---

# Promise Methods

## Promise.resolve()

Creates resolved promise.

---

## Promise.reject()

Creates rejected promise.

---

## Promise.all()

Runs multiple promises together.

---

## Promise.race()

Returns first settled promise.

---

# Promise.all Example

```js id="prth14"
Promise.all([
  Promise.resolve(1),
  Promise.resolve(2)
]).then(data => {
  console.log(data);
});
```

Output:

```js id="prth15"
[1, 2]
```

---

# Real World Use Cases

* API calls
* Database operations
* Fetch requests
* Async programming

---

# Important Points

* Promises handle async operations
* Promise has pending fulfilled rejected states
* then handles success
* catch handles errors
* Promises solve callback hell
* Promise callbacks use microtask queue

---

# Key Takeaways

* Promise represents future value
* then handles success
* catch handles failure
* Promise chaining improves readability
* Promise microtasks execute before macrotasks
