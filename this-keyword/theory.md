# JavaScript this Keyword (Deep Dive)

## What is this?

`this` refers to the object that is currently executing the function.

In simple terms:

`this` points to the current execution context.

---

# Why this is Important

* Used in objects
* Used in classes
* Used in event listeners
* Important for React
* Important for call apply bind
* Common interview topic

---

# Global this

## Browser

```js id="6y1t4n"
console.log(this);
```

Output:

```js id="fd6o7v"
window object
```

In browser, global `this` refers to `window`.

---

# this Inside Normal Function

```js id="kp4w9j"
function test() {
  console.log(this);
}

test();
```

Output in browser:

```js id="s8m2zt"
window object
```

Because normal functions use global object as `this`.

---

# this in Strict Mode

```js id="f4o7py"
"use strict";

function test() {
  console.log(this);
}

test();
```

Output:

```js id="m9x1qb"
undefined
```

In strict mode, `this` inside normal function becomes undefined.

---

# this Inside Object Method

```js id="y2t5lr"
const user = {
  name: "Kunjan",

  greet() {
    console.log(this.name);
  }
};

user.greet();
```

Output:

```js id="q7v8ns"
Kunjan
```

Why:

`this` refers to the object calling the method.

---

# this Inside Arrow Function

Arrow functions do not have their own `this`.

They inherit `this` from surrounding lexical scope.

```js id="d5r1kx"
const user = {
  name: "JavaScript",

  greet: () => {
    console.log(this.name);
  }
};

user.greet();
```

Output:

```js id="u3o9fy"
undefined
```

Why:

Arrow function takes `this` from outer/global scope.

---

# Normal Function vs Arrow Function

| Normal Function   | Arrow Function             |
| ----------------- | -------------------------- |
| Has its own this  | No own this                |
| Dynamic this      | Lexical this               |
| Depends on caller | Inherits from parent scope |

---

# this Inside Nested Function

```js id="0v4tmg"
const obj = {
  name: "JS",

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

```js id="z6k8pb"
undefined
```

Why:

`inner()` is normal function.

Its `this` becomes global object.

---

# Fix Using Arrow Function

```js id="7r3xqj"
const obj = {
  name: "JS",

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

```js id="n2w5oh"
JS
```

Why:

Arrow function inherits `this` from parent scope.

---

# this in Event Listeners

```js id="e9u1kv"
button.addEventListener("click", function () {
  console.log(this);
});
```

`this` refers to the element triggering the event.

---

# this in Constructor Function

```js id="i4m7zc"
function User(name) {
  this.name = name;
}

const user1 = new User("Kunjan");

console.log(user1.name);
```

Output:

```js id="o8q2lt"
Kunjan
```

`this` refers to newly created object.

---

# Important Points

* `this` depends on how function is called
* Arrow functions do not have their own this
* Object methods use object as this
* Normal functions use global object
* Strict mode changes this behavior

---

# Key Takeaways

* `this` refers to current execution context
* Arrow functions inherit lexical this
* Normal functions have dynamic this
* Object methods bind this to object
* Strict mode changes this to undefined
