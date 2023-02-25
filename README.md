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

## Callback Hell

```
function stepOne(value, callback) {
  setTimeout(() => {
    console.log(`Step One: ${value}`);
    callback(value + 1);
  }, 1000);
}
function stepTwo(value, callback) {
  setTimeout(() => {
    console.log(`Step Two: ${value}`);
    callback(value + 1);
  }, 1000);
}
function stepThree(value, callback) {
  setTimeout(() => {
    console.log(`Step Three: ${value}`);
    callback(value + 1);
  }, 1000);
}
function start() {
  stepOne(1, (value1) => {
    stepTwo(value1, (value2) => {
      stepThree(value2, (value3) => {
        console.log(`All Done: ${value3}`);
      });
    });
  });
}
start();
```

## Promises (Refactored)

```
function stepOne(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(`Step One: ${value}`);
      resolve(value + 1);
    }, 1000);
  });
}
function stepTwo(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(`Step Two: ${value}`);
      resolve(value + 1);
    }, 1000);
  });
}
function stepThree(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(`Step Three: ${value}`);
      resolve(value + 1);
    }, 1000);
  });
}
function start() {
  stepOne(1)
    .then(stepTwo)
    .then(stepThree)
    .then((value) => {
      console.log(`All Done: ${value}`);
    })
    .catch((error) => {
      console.error(error);
    });
}
start();
```

## Async/Await (Refactored)

```
function stepOne(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(`Step One: ${value}`);
      resolve(value + 1);
    }, 1000);
  });
}
function stepTwo(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(`Step Two: ${value}`);
      resolve(value + 1);
    }, 1000);
  });
}
function stepThree(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(`Step Three: ${value}`);
      resolve(value + 1);
    }, 1000);
  });
}
async function start() {
  try {
    let value = await stepOne(1);
    value = await stepTwo(value);
    value = await stepThree(value);
    console.log(`All Done: ${value}`);
  } catch (error) {
    console.error(error);
  }
}
start();
```

## Promise with Async/Await

```
async function stepOne(value) {
  return await new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(`Step One: ${value}`);
      resolve(value + 1);
    }, 1000);
  });
}
```

## Promise with Fetch 

```
function fetchData() {
  return new Promise((resolve, reject) => {
    fetch('https://jsonplaceholder.typicode.com/todos/1')
      .then(response => {
        if (response.ok) {
          return response.json();
        } else {
          reject('Error retrieving data');
        }
      })
      .then(data => {
        resolve(data);
      })
      .catch(error => {
        reject(error);
      });
  });
}
fetchData()
  .then(data => {
    console.log('Data:', data);
  })
  .catch(error => {
    console.error('Error:', error);
});
```

## Async/Await with Fetch

```
async function fetchData() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos/1');
    if (!response.ok) {
      throw new Error('Error retrieving data');
    }
    const data = await response.json();
    return data;
  } catch (error) {
    throw error;
  }
}
(async function () {
  try {
    const data = await fetchData();
    console.log('Data:', data);
  } catch (error) {
    console.error('Error:', error);
  }
})();
```

## Async/Await with Fetch (Refactored)

```
async function fetchData() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos/1');
    if (!response.ok) {
      throw new Error('Error retrieving data');
    }
    const data = await response.json();
    console.log('Data:', data);
  } catch (error) {
    console.error('Error:', error);
  }
}
fetchData();
```

## Tutorial

https://youtu.be/IDn16Y8A3Ww

WebStylePress https://www.youtube.com/@webstylepress
