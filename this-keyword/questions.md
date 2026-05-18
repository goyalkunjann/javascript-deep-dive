# JavaScript this Keyword Questions

# Theory Questions

## Q1

What is this keyword in JavaScript?

Answer:

`this` refers to the object currently executing the function.

---

## Q2

How does this behave in global scope?

Answer:

In browser:
global `this` refers to window object.

---

## Q3

What is this inside normal function?

Answer:

In browser:
normal function uses global object as `this`.

In strict mode:
`this` becomes undefined.

---

## Q4

What is this inside object method?

Answer:

`this` refers to the object calling the method.

---

## Q5

What is lexical this?

Answer:

Arrow functions inherit `this` from surrounding scope.

---

## Q6

Difference between normal function and arrow function this?

Answer:

| Normal Function | Arrow Function |
| --------------- | -------------- |
| Own this        | No own this    |
| Dynamic this    | Lexical this   |

---

## Q7

Why do arrow functions not have their own this?

Answer:

Arrow functions inherit this from parent lexical scope.

---

## Q8

How does strict mode affect this?

Answer:

In strict mode:
this inside normal function becomes undefined.

---

## Q9

What is this inside event listener?

Answer:

`this` refers to the element triggering the event.

---

## Q10

What is this inside constructor function?

Answer:

`this` refers to newly created object.

---

# Practical Coding Questions

## Q11

```js id="q2k7mr"
console.log(this);
```

Output:

```js id="d8p4xt"
window object
```

---

## Q12

```js id="w5n1qb"
function test() {
  console.log(this);
}

test();
```

Output:

```js id="u9r6zc"
window object
```

---

## Q13

```js id="f3o8lh"
"use strict";

function test() {
  console.log(this);
}

test();
```

Output:

```js id="i7m2yv"
undefined
```

---

## Q14

```js id="e4t9ks"
const user = {
  name: "Kunjan",

  greet() {
    console.log(this.name);
  }
};

user.greet();
```

Output:

```js id="p1w5dn"
Kunjan
```

---

## Q15

```js id="c6y2ra"
const user = {
  name: "JS",

  greet: () => {
    console.log(this.name);
  }
};

user.greet();
```

Output:

```js id="j8u7mx"
undefined
```

---

## Q16

```js id="n0k3vb"
const obj = {
  name: "JavaScript",

  test() {
    function inner() {
      console.log(this.name);
    }

    inner();
  }
};

obj.test();
```

Output:

```js id="b4f9wp"
undefined
```

---

## Q17

```js id="t5l1oq"
const obj = {
  name: "JavaScript",

  test() {
    const inner = () => {
      console.log(this.name);
    };

    inner();
  }
};

obj.test();
```

Output:

```js id="r7x3hy"
JavaScript
```

---

## Q18

```js id="g8m6cu"
function User(name) {
  this.name = name;
}

const user1 = new User("Kunjan");

console.log(user1.name);
```

Output:

```js id="o2v9qa"
Kunjan
```

---

## Q19

```js id="l1r4pn"
const obj = {
  name: "JS",

  getName() {
    return this.name;
  }
};

console.log(obj.getName());
```

Output:

```js id="y5k8tb"
JS
```

---

## Q20

```js id="z3q7wv"
const obj = {
  name: "Frontend",

  show() {
    console.log(this.name);
  }
};

const fn = obj.show;

fn();
```

Output:

```js id="h6u1cx"
undefined
```

Why:

Function lost object reference.
