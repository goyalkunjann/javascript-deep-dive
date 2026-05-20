# JavaScript Callbacks (Deep Dive)

# What is a Callback Function?

A callback function is a function passed as argument to another function.

The callback function is executed later.

---

# Why Callbacks are Important

Callbacks are used to:

* handle asynchronous operations
* execute functions later
* improve code reusability
* handle events

---

# Basic Callback Example

```js id="cbth1"
function greet(name, callback) {
  console.log("Hello " + name);

  callback();
}

function sayBye() {
  console.log("Bye");
}

greet("Kunjan", sayBye);
```

Output:

```js id="cbth2"
Hello Kunjan
Bye
```

---

# Functions are First Class Citizens

Callbacks are possible because functions are first class citizens.

Functions can:

* be passed
* stored
* returned

---

# Synchronous Callback

A callback executed immediately.

Example:

```js id="cbth3"
function process(callback) {
  callback();
}

process(() => {
  console.log("Executed");
});
```

Output:

```js id="cbth4"
Executed
```

---

# Asynchronous Callback

A callback executed later.

Example:

```js id="cbth5"
setTimeout(() => {
  console.log("Executed Later");
}, 1000);
```

Output after 1 second:

```js id="cbth6"
Executed Later
```

---

# setTimeout Callback

```js id="cbth7"
console.log("Start");

setTimeout(() => {
  console.log("Callback");
}, 0);

console.log("End");
```

Output:

```js id="cbth8"
Start
End
Callback
```

Why:

`setTimeout` callback goes to callback queue and executes after call stack becomes empty.

---

# Event Listener Callback

```js id="cbth9"
button.addEventListener("click", () => {
  console.log("Button Clicked");
});
```

The callback executes only when event occurs.

---

# Callback Hell

Nested callbacks creating unreadable code.

Example:

```js id="cbth10"
setTimeout(() => {
  console.log("Step 1");

  setTimeout(() => {
    console.log("Step 2");

    setTimeout(() => {
      console.log("Step 3");
    }, 1000);

  }, 1000);

}, 1000);
```

This structure becomes difficult to manage.

---

# Problems with Callback Hell

* unreadable code
* difficult debugging
* hard maintenance
* nested pyramid structure

---

# Inversion of Control

When we pass callback to another function,
we lose control over execution.

Example:

```js id="cbth11"
apiCall(function () {
  console.log("Executed");
});
```

We trust `apiCall` to execute callback correctly.

---

# Why Promises were Introduced

Promises solve:

* callback hell
* inversion of control

---

# Real World Uses of Callbacks

* Event listeners
* API calls
* setTimeout
* Database operations
* File reading

---

# Important Points

* Callback is function passed into another function
* Callbacks can be synchronous or asynchronous
* setTimeout uses asynchronous callback
* Nested callbacks create callback hell
* Promises solve callback problems

---

# Key Takeaways

* Callback = function passed into another function
* JavaScript uses callbacks heavily
* Async operations use callbacks
* Callback hell makes code messy
* Promises improve async handling
