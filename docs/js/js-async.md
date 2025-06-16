# Async JavaScript and HTTP Requests

## Promises

## Async Await

`async...await` is **syntactic sugar**, which introduces new syntax for using promises and generators.

It does **NOT** increases the speed of a promise resolving.

### Concurrency

We should only halt and wait for an execution unless we absolutely need to, aka there are other operations dependent on it.

```js
// Dependent
async function doLaundry() {
  const wash = await washClothes();
  const dry = await dryClothes(wash);
  const fold = await foldClothes(dry);
  console.log("Laundry is done!");
}

//Independent, or concurrent
async function selfCare() {
  const skincare = skincareRoutine();
  const relax = watchMovie();
  const dinner = orderTakeout();
  console.log(
    `Self-care Saturday! ${await skincare}, ${await watchMovie}, and ${await orderTakeout}`
  );
}
```

### 3 different ways to read two files sequentially

#### `fs.readfile()`

```js
const fs = require("fs");

fs.readFile("./file.txt", "utf-8", (err, data) => {
  if (err) throw err;
  let firstSentence = data;
  fs.readFile("./file2.txt", "utf-8", (err, data) => {
    if (err) throw err;
    let secondSentence = data;
    console.log(firstSentence, secondSentence);
  });
});
```

#### Native promise syntax

```js
const promisifiedReadfile = require("./promisifiedReadfile");

let firstSentence;
promisifiedReadfile("./file.txt", "utf-8")
  .then((data) => {
    firstSentence = data;
    return promisifiedReadfile("./file2.txt", "utf-8");
  })
  .then((data) => {
    let secondSentence = data;
    console.log(firstSentence, secondSentence);
  })
  .catch((err) => {
    console.log(err);
  });
```

#### await/async

```js
const promisifiedReadfile = require("./promisifiedReadfile");

async function readFiles() {
  let firstSentence = await promisifiedReadfile("./file.txt", "utf-8");
  let secondSentence = await promisifiedReadfile("./file2.txt", "utf-8");
  console.log(firstSentence, secondSentence);
}

readFiles();
```

### How to refactor a promise to async

```js title="nativePromise.js"
function nativePromise() {
  return new Promise((resolve, reject) => {
    resolve("yay!");
  });
}
```

```js title="asyncPromise.js"
async function asyncPromise() {
  return "yay!";
}
```
