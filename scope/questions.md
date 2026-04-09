# JavaScript Scope Questions

---

## Q1

```js
console.log(a);
var a = 10;
```

**Output:**
undefined

**Why:**
`var` is hoisted and initialized with `undefined`

---

## Q2

```js
console.log(a);
let a = 10;
```

**Output:**
ReferenceError

**Why:**
`let` is in Temporal Dead Zone (TDZ) before initialization

---

## Q3

```js
function test() {
  console.log(a);
  var a = 20;
}
test();
```

**Output:**
undefined

**Why:**
Local `var a` is hoisted inside the function

---

## Q4

```js
var a = 10;

function test() {
  console.log(a);
}

test();
```

**Output:**
10

**Why:**
Function accesses variable from global scope

---

## Q5

```js
var a = 10;

function test() {
  var a = 20;
  console.log(a);
}

test();
```

**Output:**
20

**Why:**
Local variable shadows global variable

---

## Q6

```js
let a = 10;

{
  let a = 20;
}

console.log(a);
```

**Output:**
10

**Why:**
Block scope shadowing does not affect outer variable

---

## Q7

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

**Output:**
3 3 3

**Why:**
`var` is function scoped, so same variable is shared

---

## Q8

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

**Output:**
0 1 2

**Why:**
`let` creates a new variable for each iteration

---

## Q9

```js
let a = 1;

function outer() {
  let a = 2;

  function inner() {
    console.log(a);
  }

  inner();
}

outer();
```

**Output:**
2

**Why:**
Lexical scope — inner function accesses nearest variable

---

## Q10

```js
let a = 1;

function outer() {
  let a = 2;

  function inner() {
    console.log(a);
  }

  return inner;
}

outer()();
```

**Output:**
2

**Why:**
Closure retains lexical scope

---

## Q11

```js
var a = 1;

function outer() {
  var a = 2;
  inner();
}

function inner() {
  console.log(a);
}

outer();
```

**Output:**
1

**Why:**
Scope depends on where function is defined, not called

---

## Q12

```js
function test() {
  console.log(a);
}
var a = 10;

test();
```

**Output:**
10

**Why:**
Variable `a` is in global scope

---

## Q13

```js
{
  var a = 10;
}
console.log(a);
```

**Output:**
10

**Why:**
`var` is not block scoped

---

## Q14

```js
{
  let a = 10;
}
// console.log(a);
```

**Output:**
ReferenceError

**Why:**
`let` is block scoped

---

## Q15

```js
let a = 10;

function test() {
  console.log(a);
  let a = 20;
}

test();
```

**Output:**
ReferenceError

**Why:**
Accessing `a` before initialization (TDZ)

---

## Q16

```js
function test() {
  var a = 10;
  return function () {
    console.log(a);
  };
}

const fn = test();
fn();
```

**Output:**
10

**Why:**
Closure retains reference to variable

---

## Q17

```js
var a = 10;

function test() {
  console.log(a);
  var a = 20;
}

test();
```

**Output:**
undefined

**Why:**
Local variable is hoisted

---

## Q18

```js
let a = 10;

function test() {
  if (true) {
    let a = 20;
    console.log(a);
  }
}

test();
```

**Output:**
20

**Why:**
Block scope inside `if`

---

## Q19

```js
var a = 10;

function test() {
  console.log(a);
}

function test2() {
  var a = 20;
  test();
}

test2();
```

**Output:**
10

**Why:**
Lexical scope (definition scope is used)

---

## Q20 (Advanced)

```js
for (var i = 0; i < 3; i++) {
  (function(i) {
    setTimeout(() => console.log(i), 100);
  })(i);
}
```

**Output:**
0 1 2

**Why:**
IIFE creates a new scope for each iteration
