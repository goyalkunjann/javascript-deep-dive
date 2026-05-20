# JavaScript Async Await Questions

# Theory Questions

## Q1

What is async await?

Answer:

A cleaner way to handle Promises.

---

## Q2

What does async keyword do?

Answer:

Makes function return a Promise.

---

## Q3

What does await do?

Answer:

Waits for Promise resolution.

---

## Q4

Can await be used outside async function?

Answer:

No.

---

## Q5

Does async function always return Promise?

Answer:

Yes.

---

## Q6

Why is async await better than promise chaining?

Answer:

Cleaner and easier to read.

---

## Q7

How is error handled in async await?

Answer:

Using try catch.

---

## Q8

Does await block JavaScript?

Answer:

No.

It pauses only async function execution.

---

## Q9

Can async await replace Promises?

Answer:

No.

async await is built on top of Promises.

---

## Q10

What happens if Promise rejects inside await?

Answer:

Control goes to catch block.

---

# Practical Coding Questions

## Q11

```js id="aaq1"
async function test() {
  return "Hello";
}

test().then(data => {
  console.log(data);
});
```

Output:

```js id="aaq2"
Hello
```

---

## Q12

```js id="aaq3"
function fetchData() {
  return Promise.resolve("Data");
}

async function getData() {
  const data = await fetchData();

  console.log(data);
}

getData();
```

Output:

```js id="aaq4"
Data
```

---

## Q13

```js id="aaq5"
async function test() {
  return 100;
}

console.log(test());
```

Output:

```js id="aaq6"
Promise
```

---

## Q14

```js id="aaq7"
async function test() {
  const value = await Promise.resolve(50);

  console.log(value);
}

test();
```

Output:

```js id="aaq8"
50
```

---

## Q15

```js id="aaq9"
async function test() {
  try {
    await Promise.reject("Error");

  } catch (err) {
    console.log(err);
  }
}

test();
```

Output:

```js id="aaq10"
Error
```

---

## Q16

```js id="aaq11"
console.log("Start");

async function test() {
  console.log("Inside");

  await Promise.resolve();

  console.log("After Await");
}

test();

console.log("End");
```

Output:

```js id="aaq12"
Start
Inside
End
After Await
```

---

## Q17

```js id="aaq13"
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

```js id="aaq14"
Done
```

---

## Q18

```js id="aaq15"
async function test() {
  return Promise.resolve("Resolved");
}

test().then(data => {
  console.log(data);
});
```

Output:

```js id="aaq16"
Resolved
```

---

## Q19

```js id="aaq17"
console.log("A");

async function test() {
  console.log("B");

  await Promise.resolve();

  console.log("C");
}

test();

console.log("D");
```

Output:

```js id="aaq18"
A
B
D
C
```

---

## Q20

```js id="aaq19"
async function test() {
  const value1 = await Promise.resolve(1);

  const value2 = await Promise.resolve(2);

  console.log(value1 + value2);
}

test();
```

Output:

```js id="aaq20"
3
```

---

## Q21

```js id="aaq21"
async function test() {
  throw "Error";
}

test().catch(err => {
  console.log(err);
});
```

Output:

```js id="aaq22"
Error
```

---

## Q22

```js id="aaq23"
console.log("1");

async function test() {
  console.log("2");

  await Promise.resolve();

  console.log("3");
}

test();

console.log("4");
```

Output:

```js id="aaq24"
1
2
4
3
```

---

## Q23

```js id="aaq25"
async function test() {
  return await Promise.resolve("Hello");
}

test().then(data => {
  console.log(data);
});
```

Output:

```js id="aaq26"
Hello
```

---

## Q24

```js id="aaq27"
async function test() {
  try {
    const result = await Promise.resolve("Success");

    console.log(result);

  } catch (err) {
    console.log(err);
  }
}

test();
```

Output:

```js id="aaq28"
Success
```

---

## Q25 — GOLDMAN SACHS STYLE

```js id="aaq29"
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

async function test() {
  console.log("3");

  await Promise.resolve();

  console.log("4");
}

test();

Promise.resolve().then(() => {
  console.log("5");
});

console.log("6");
```

Output:

```js id="aaq30"
1
3
6
4
5
2
```
