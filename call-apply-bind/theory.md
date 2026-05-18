# JavaScript call apply bind (Deep Dive)

## What are call apply bind?

`call`, `apply`, and `bind` are methods used to control the value of `this` inside a function.

In simple terms:

They allow us to manually set `this`.

---

# Why call apply bind are Important

* Change `this` manually
* Function borrowing
* Reuse functions
* Important for interviews
* Used in React and JavaScript internals

---

# Function Borrowing

One object can borrow methods from another object using:

* call
* apply
* bind

---

# call()

`call()` invokes a function immediately and allows passing arguments individually.

Syntax:

```js id="d2w6p8"
functionName.call(thisArg, arg1, arg2)
```

---

# Example

```js id="z6f3n1"
const user1 = {
  name: "Kunjan"
};

function greet(city) {
  console.log(this.name + " from " + city);
}

greet.call(user1, "Delhi");
```

Output:

```js id="p4v8q2"
Kunjan from Delhi
```

Why:

`this` points to `user1`.

---

# apply()

`apply()` works like call but arguments are passed as array.

Syntax:

```js id="t7j1x9"
functionName.apply(thisArg, [args])
```

---

# Example

```js id="k9u4m3"
const user1 = {
  name: "JavaScript"
};

function greet(city, country) {
  console.log(this.name + " from " + city + ", " + country);
}

greet.apply(user1, ["Delhi", "India"]);
```

Output:

```js id="b5r7n0"
JavaScript from Delhi, India
```

---

# Difference Between call and apply

| call                 | apply                |
| -------------------- | -------------------- |
| Arguments separately | Arguments as array   |
| Executes immediately | Executes immediately |

---

# bind()

`bind()` does not invoke function immediately.

It returns a new function with bound `this`.

Syntax:

```js id="y8h2v5"
functionName.bind(thisArg)
```

---

# Example

```js id="o1m6r4"
const user = {
  name: "Frontend"
};

function greet() {
  console.log(this.name);
}

const fn = greet.bind(user);

fn();
```

Output:

```js id="u3x9t7"
Frontend
```

Why:

`bind()` returns new function with fixed `this`.

---

# Difference Between call apply bind

| Method | Invokes Immediately | Arguments |
| ------ | ------------------- | --------- |
| call   | Yes                 | Separate  |
| apply  | Yes                 | Array     |
| bind   | No                  | Separate  |

---

# call with Multiple Arguments

```js id="g4n8k2"
const person = {
  name: "Kunjan"
};

function intro(age, city) {
  console.log(this.name, age, city);
}

intro.call(person, 22, "Delhi");
```

Output:

```js id="r9y5w1"
Kunjan 22 Delhi
```

---

# apply with Multiple Arguments

```js id="q7e1v3"
const person = {
  name: "React"
};

function intro(age, city) {
  console.log(this.name, age, city);
}

intro.apply(person, [22, "Noida"]);
```

Output:

```js id="h2p6n9"
React 22 Noida
```

---

# bind Example

```js id="n8v4c1"
const user = {
  name: "JavaScript"
};

function show() {
  console.log(this.name);
}

const boundFn = show.bind(user);

boundFn();
```

Output:

```js id="f6k2x5"
JavaScript
```

---

# Function Borrowing Example

```js id="m3z7q8"
const user1 = {
  name: "Kunjan"
};

const user2 = {
  name: "Frontend"
};

function greet() {
  console.log(this.name);
}

greet.call(user1);
greet.call(user2);
```

Output:

```js id="w9r4t1"
Kunjan
Frontend
```

---

# Important Points

* call apply bind change `this`
* call and apply execute immediately
* bind returns new function
* apply accepts arguments as array
* bind is heavily used in event handlers and React

---

# Real World Use Cases

## 1. Function Borrowing

Reuse methods between objects.

---

## 2. Event Handlers

Maintain correct `this`.

---

## 3. React Class Components

Binding event methods.

---

# Key Takeaways

* call apply bind manually control this
* call uses separate arguments
* apply uses array arguments
* bind returns new function
* Important for object methods and function borrowing
