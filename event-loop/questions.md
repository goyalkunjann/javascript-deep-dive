# JavaScript Event Loop Questions

# Theory Questions

## Q1

What is Event Loop?

Answer:

Event Loop is a mechanism that handles asynchronous operations in JavaScript.

---

## Q2

Why is Event Loop needed?

Answer:

Because JavaScript is single-threaded and cannot execute async operations directly.

---

## Q3

What are Web APIs?

Answer:

Browser-provided APIs like:

* setTimeout
* fetch
* DOM APIs
* event listeners

---

## Q4

What is Callback Queue?

Answer:

Queue storing async callbacks waiting for execution.

---

## Q5

What does Event Loop do?

Answer:

It checks:

* is call stack empty?

If yes:

* moves callback from queue to stack.

---

## Q6

Does setTimeout guarantee exact timing?

Answer:

No.

It guarantees minimum delay only.

---

## Q7

Why does setTimeout with 0ms still wait?

Answer:

Because callback waits for call stack to become empty.

---

## Q8

Difference between synchronous and asynchronous code?

| Synchronous          | Asynchronous   |
| -------------------- | -------------- |
| Executes immediately | Executes later |

---

## Q9

Can Event Loop work without Call Stack?

Answer:

No.

Event Loop works together with call stack.

---

## Q10

Why does infinite loop block JavaScript?

Answer:

Because it blocks call stack.

---

# Practical Coding Questions

## Q11

```js id="evq1"
console.log("Start");

setTimeout(() => {
  console.log("Callback");
}, 0);

console.log("End");
```

Output:

```js id="evq2"
Start
End
Callback
```

---

## Q12

```js id="evq3"
setTimeout(() => {
  console.log("Hello");
}, 1000);

console.log("Done");
```

Output:

```js id="evq4"
Done
Hello
```

---

## Q13

```js id="evq5"
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

console.log("C");
```

Output:

```js id="evq6"
A
C
B
```

---

## Q14

```js id="evq7"
console.log("Start");

setTimeout(() => {
  console.log("Inside Timeout");
}, 2000);

console.log("End");
```

Output:

```js id="evq8"
Start
End
Inside Timeout
```

---

## Q15

```js id="evq9"
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

setTimeout(() => {
  console.log("3");
}, 0);

console.log("4");
```

Output:

```js id="evq10"
1
4
2
3
```

---

## Q16

```js id="evq11"
console.log("Start");

while (true) {}

console.log("End");
```

Output:

```js id="evq12"
Start
```

Why:

Infinite loop blocks call stack.

---

## Q17

```js id="evq13"
setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("Immediate");
```

Output:

```js id="evq14"
Immediate
Timeout
```

---

## Q18

```js id="evq15"
console.log("A");

function test() {
  console.log("B");
}

setTimeout(test, 0);

console.log("C");
```

Output:

```js id="evq16"
A
C
B
```

---

## Q19

```js id="evq17"
console.log("Start");

setTimeout(() => {
  console.log("Callback 1");
}, 1000);

setTimeout(() => {
  console.log("Callback 2");
}, 500);

console.log("End");
```

Output:

```js id="evq18"
Start
End
Callback 2
Callback 1
```

---

## Q20

```js id="evq19"
console.log("A");

setTimeout(() => {
  console.log("B");

  setTimeout(() => {
    console.log("C");
  }, 0);

}, 0);

console.log("D");
```

Output:

```js id="evq20"
A
D
B
C
```

---

## Q21

```js id="evq21"
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

for (let i = 0; i < 1000000000; i++) {}

console.log("End");
```

Output:

```js id="evq22"
Start
End
Timeout
```

Why:

Heavy synchronous code blocks call stack.

---

## Q22

```js id="evq23"
console.log(typeof setTimeout);
```

Output:

```js id="evq24"
function
```

---

## Q23

```js id="evq25"
setTimeout(() => {
  console.log("Executed");
}, 0);

console.log("Main Thread");
```

Output:

```js id="evq26"
Main Thread
Executed
```

---

## Q24

```js id="evq27"
console.log("X");

setTimeout(() => {
  console.log("Y");
}, 100);

console.log("Z");
```

Output:

```js id="evq28"
X
Z
Y
```

---

## Q25 — GOLDMAN SACHS STYLE

```js id="evq29"
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

```js id="evq30"
1
4
3
2
```

Why:

Promise callbacks (microtasks) execute before setTimeout callbacks (macrotasks).
