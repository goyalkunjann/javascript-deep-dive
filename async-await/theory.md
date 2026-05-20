# JavaScript Async Await (Deep Dive)

# What is async await?

`async await` is a cleaner way to handle Promises.

It makes asynchronous code look synchronous.

---

# Why async await is Important

* Cleaner syntax
* Easier to read
* Easier error handling
* Avoids promise chaining complexity
* Common interview topic

---

# async Function

An `async` function always returns a Promise.

Example:

```js id="aath1"
async function test() {
  return "Hello";
}

test().then(data => {
  console.log(data);
});
```

Output:

```js id="aath2"
Hello
```

---

# await Keyword

`await` waits for Promise resolution.

It can only be used inside async function.

---

# Basic Example

```js id="aath3"
function fetchData() {
  return Promise.resolve("Data Received");
}

async function getData() {
  const data = await fetchData();

  console.log(data);
}

getData();
```

Output:

```js id="aath4"
Data Received
```

---

# async await Flow

## Step 1

Function marked async.

---

## Step 2

`await` pauses execution temporarily.

---

## Step 3

Promise resolves.

---

## Step 4

Execution resumes.

---

# await with setTimeout

```js id="aath5"
function delay() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve("Done");
    }, 1000);
  });
}

async function run() {
  const result = await delay();

  console.log(result);
}

run();
```

Output after 1 second:

```js id="aath6"
Done
```

---

# Error Handling using try catch

```js id="aath7"
async function test() {
  try {
    const result = await Promise.reject("Error");

    console.log(result);

  } catch (err) {
    console.log(err);
  }
}

test();
```

Output:

```js id="aath8"
Error
```

---

# async await vs Promise Chaining

| Promise Chaining | Async Await    |
| ---------------- | -------------- |
| Multiple then()  | Cleaner syntax |
| Harder to read   | Easier to read |

---

# async Function Always Returns Promise

```js id="aath9"
async function test() {
  return 10;
}

console.log(test());
```

Output:

```js id="aath10"
Promise
```

Why:

Async functions automatically wrap values in Promise.

---

# await Only Works with Promises

```js id="aath11"
async function test() {
  const value = await Promise.resolve(100);

  console.log(value);
}

test();
```

Output:

```js id="aath12"
100
```

---

# Real World Use Cases

* API calls
* Fetch requests
* Database operations
* Authentication
* Async programming

---

# Important Points

* async functions return promises
* await pauses execution
* await works inside async functions
* try catch handles errors
* async await improves readability

---

# Key Takeaways

* async await simplifies promises
* async always returns promise
* await waits for promise resolution
* try catch handles async errors
* async await makes async code cleaner
