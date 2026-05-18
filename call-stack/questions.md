# JavaScript Call Stack Questions

# Theory Questions

## Q1

What is Call Stack in JavaScript?

Answer:

Call Stack is a mechanism that stores execution contexts and manages function execution order.

---

## Q2

What does LIFO mean?

Answer:

LIFO means:

```js id="2d8n4n"
Last In First Out
```

The last function added to stack is removed first.

---

## Q3

Why is JavaScript single-threaded?

Answer:

JavaScript has:

* one call stack
* one thread of execution

So it executes one operation at a time.

---

## Q4

What is a Stack Frame?

Answer:

Each execution context inside call stack is called a stack frame.

---

## Q5

What happens when a function is invoked?

Answer:

A new Function Execution Context is pushed into call stack.

---

## Q6

What happens after function execution completes?

Answer:

Its execution context is popped out from stack.

---

## Q7

What is Stack Overflow?

Answer:

When call stack memory becomes full due to too many function calls.

---

## Q8

What causes Maximum Call Stack Size Exceeded?

Answer:

Infinite recursion or excessive nested function calls.

---

## Q9

Difference between Execution Context and Call Stack?

Answer:

| Execution Context               | Call Stack                |
| ------------------------------- | ------------------------- |
| Environment where code executes | Stores execution contexts |
| Created during execution        | Manages execution order   |

---

## Q10

How does Call Stack relate to Event Loop?

Answer:

Event Loop checks whether call stack is empty before pushing callbacks into stack.

---

# Practical Coding Questions

## Q11

```js id="ctk9jp"
function one() {
  console.log("One");
}

one();
```

Output:

```js id="kmh7v8"
One
```

Explain stack flow.

Answer:

```js id="jcvnq0"
Global()
↓
one()
↓
POP one()
↓
POP Global()
```

---

## Q12

```js id="5f4k2n"
function one() {
  two();
}

function two() {
  console.log("Two");
}

one();
```

Output:

```js id="j9k7x1"
Two
```

Explain stack flow.

Answer:

```js id="ek4o7w"
Global()
↓
one()
↓
two()
↓
POP two()
↓
POP one()
↓
POP Global()
```

---

## Q13

```js id="umvgoz"
function first() {
  console.log("First");
  second();
}

function second() {
  console.log("Second");
}

first();
```

Output:

```js id="50knwl"
First
Second
```

Explain execution order.

Answer:

* first() pushed
* second() pushed
* second() removed
* first() removed

---

## Q14

```js id="8nd7d9"
function a() {
  b();
}

function b() {
  c();
}

function c() {
  console.log("C");
}

a();
```

Output:

```js id="sl7d73"
C
```

Explain stack flow.

Answer:

```js id="5nyh9l"
Global()
↓
a()
↓
b()
↓
c()
↓
POP c()
↓
POP b()
↓
POP a()
```

---

## Q15

```js id="kjg10k"
function test() {
  test();
}

test();
```

Output:

```js id="7pg6j4"
RangeError: Maximum call stack size exceeded
```

Why:

Infinite recursion continuously fills call stack.

---

## Q16

```js id="73n4ut"
console.log("Start");

function test() {
  console.log("Inside Test");
}

test();

console.log("End");
```

Output:

```js id="1c78n6"
Start
Inside Test
End
```

Explain execution order.

Answer:

```js id="l0v76w"
Global()
↓
test()
↓
POP test()
↓
continue global execution
```

---

## Q17

```js id="1wy17j"
function one() {
  console.log("One");
}

function two() {
  console.log("Two");
}

one();
two();
```

Output:

```js id="v0y8g0"
One
Two
```

Explain stack behavior.

Answer:

Functions execute one after another using LIFO.

---

## Q18

```js id="9o7g7j"
function outer() {
  function inner() {
    console.log("Inner");
  }

  inner();
}

outer();
```

Output:

```js id="csqkh6"
Inner
```

Explain execution contexts created.

Answer:

```js id="xvm5m4"
Global()
↓
outer()
↓
inner()
↓
POP inner()
↓
POP outer()
```

---

## Q19

```js id="scn1vg"
function one() {
  console.log("One");
  two();
}

function two() {
  console.log("Two");
  three();
}

function three() {
  console.log("Three");
}

one();
```

Output:

```js id="dg7sn8"
One
Two
Three
```

Explain full stack flow.

Answer:

```js id="x87lv2"
Global()
↓
one()
↓
two()
↓
three()
↓
POP three()
↓
POP two()
↓
POP one()
```

---

## Q20

```js id="8s7l0t"
function test() {
  return "JavaScript";
}

console.log(test());
```

Output:

```js id="d48qpi"
JavaScript
```

Explain stack behavior.

Answer:

```js id="3bxr3v"
Global()
↓
test()
↓
return value
↓
POP test()
```
