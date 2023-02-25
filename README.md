# Callback Hell, Promises, Async-Await 

## Callback

```
// .............................. //
// JavaScript Callback Functions
// A function passed to another function as an argument
// .............................. //

// Main function calling the callback function
function greet(name, callback) {
  console.log(`Hello ${name}!`);
  // callback function call
  callback();
}

// this is callback function
function ask() {
  setTimeout(() => {
    console.log('How are you?');
  }, 2000);
}

greet('John', ask);
```
