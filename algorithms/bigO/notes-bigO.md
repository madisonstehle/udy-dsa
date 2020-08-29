# Big O Notation

How do we know what the "best" way to solve a problem is? With Big O, we can evaluate multiple implementations of the same function.

## Resources
- [Performance Tracker](https://rithmschool.github.io/function-timer-demo/)

## Why do we Care?
- It's important to have a precise vocabulary to talk about how our code performs. 
- Useful for discussing trade-offs between different approaches.
- When your code slows down or crashes, identifying parts of the code that are inefficient can help us find pain points in our applications.

## Time Complexity
> Analyzing the runtime of an algorithm as the size of inputs increases.

### Let's do an example:

Let's write a function that calculates the sum of all numbers from 1 up to (and including) some number `n`. input `n = 3` outputs `6`.

```js
// V1

function addUpTo(n) {
  let total = 0;

  for (let i = 1; i <= n; i++) {
    total += i;
  }

  return total;
}
```
VS.
```js
// V2

function addUpTo(n) {
  return n * (n + 1) / 2;
}
```
_[Click here for the math behind V2...](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/learn/lecture/8344046?start=152#notes)_


#### How can I evaluate this?

One way is to literally measure the amount of time:

```js
// using `performance.now()` with the `addUpTo()` function

let t1 = performance.now();
addUpTo(10000000);
let t2 = performance.now();
console.log(`Time Elapsed: ${(t2 - t1) / 1000} seconds.`);
```

However, using this method can present problems like:
- Different machines will record different times
- The same machine can even record different times!
- For really fast algorithms, speed measurements may not be precise enough.

So, rather than counting seconds, you can can count **_the number of simple operations_** the computer has to perform.

With our **V2** `addUpTo(n)` function, it's simple to count our operations. There are **three**: multiply, add, divide. These three actions do not change as `n` changes. This means that this is **constant time or O(1)**

However, with our **V2** function, the number of operations is variable to the value of `n` = `n` number of operations! All of the variable assignments, increments, and addition operations scale as `n` grows. If `n` doubles, then the number of operations will also roughly double. This means we could be as high as 5n + 2 or as low as 2n, but _regardless of the exact value of `n`, we are focused on the proportion of operations as `n` changes_! So, this is **linear time or O(n)**

### Another Example
Let's write a function that prints all the pairs up to a given number `n`.

```js
function printAllPairs(n) {
  for (let i = 0; i < n; i++) {
    for (let j = 0; j < n; j++) {
      console.log(i, j);
    }
  }
}
```
Here we have an O(n) operation inside of an O(n) operation, which means that for each run of `n`, it runs `n * n` times. This leads us to **quadratic time or O(n<sup>2</sup>)**

### Tips & Tricks
1. Constants and small terms don't matter.
  - O(2n) = O(n)
  - O(n + 10) = O(n)
  - O(500) = O(1)
  - O(13n<sup>2</sup>) = O(n<sup>2</sup>)
  - O(n<sup>2</sup> + 5n + 8) = O(n<sup>2</sup>)
2. Arithmetic operations are constant.
3. Variable assignment is constant.
4. Accessing elements in an array by index or an object by key is constant.
5. In a loop, the complexity is the length of the loop times the complexity of whatever happens inside the loop.


## Space Complexity
> Analyzing how much additional memory we need to allocate in order to run the algorithm.

### Tips & Tricks
1. Most primitives (booleans, numbers, `undefined`, `null`) are constant space
2. Strings require O(n) space (where n is the string length)
3. Reference types are generally O(n), where n is the length (for arrays) or the number of keys (for objects)

### For Example
In the following function, we have two declarations. One for the variable `total`, which is just a number, and one for the variable `i`, which is just another number. No matter what the size of the input is, it doesn't have an impact on the number of declarations or the size of those variables. A number takes up constant space. This puts the space complexity of this function at **constant space or O(1)**.

```js
function sum(arr) {
  let total = 0;
  for (let i = 0; i < arr.length; i++) {
    total += arr[i];
  }
  return total;
}
```

Let's try another one. In the below function, we are creating a new array, no matter what, so that declaration stays the same. _however_, the length of the array, or the space it takes up, is directly proportionate to the size of the input. As the input grows, so does the space that our new array takes up. This means that the space complexity here is **linear time or O(n)**
```js
function double(arr) {
  let newArr = [];
  for (let i = 0; i < arr.length; i++) {
    newArr.push(2 * arr[i]);
  }
  return newArr;
}
```

## Logarithms
Math stuff. Lots o math stuff. One way of thinking about logs is as the inverse of exponentiation. You can also use the idea that the logarithm of a number roughly measures the number of times you can divide that number by 2 _before you get a value that's less than or equal to one_.


For example: 
  - log<sub>2</sub>(8) = 3 `->` 2<sup>3</sup> = 8
  - log<sub>base</sub>(value) = exponent `->` base<sup>exponent</sup> = value

### What good is a log?
- Certain searching algorithms have logarithmic time complexity
- Efficient sorting algorithms involve logarithms
- Recursion sometimes involves logarithmic space complexity

## Look a Graph!
![Big O Complexity Chart](../../assets/bigOGraph.jpeg)

## Vocabulary
- **Big O**: A way to talk formally about how the runtime of an algorithm grows as the inputs grow. This focuses on trends, rather than the details. Most of the time, this refers to a worst-case scenario.
- **O(f(n))**: The number of simple operations the computer has to do is eventually less than a constant times f(n), as n increases.
  - f(n) could be linear - (f(n) = n)
  - f(n) could be quadratic - (f(n) = n<sup>2</sup>)
  - f(n) could be constant - (f(n) = 1)
  - f(n) could be something entirely different
- **Time Complexity**: Analyzing the runtime of an algorithm as the size of inputs increases.
- **Space Complexity**: Analyzing how much additional memory we need to allocate in order to run the algorithm.
  - If you hear **Auxiliary Space Complexity**, that refers to the space required by the algorithm _not including_ space taken up by the inputs. Most of the time, this is what we're talking about when we say space complexity.