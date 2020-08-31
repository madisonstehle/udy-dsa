# Problem Solving Approach

Almost everything that you do in programming involves some kind of algorithm. This is the foundation for being a successful problem solver and developer.

We can improve in problem solving by...
1. Devising a plan for solving problems
2. Mastering common problem solving patterns


## Resources
- [_How To Solve It_ by George Polya]()


## Problem Solving Steps

### 1. Understand the Problem
Do a thorough investigation of the problem! Asking yourself and the potential interviewer questions like
1. Can I restate the problem in my own words?
2. What are the inputs that go into the problem?
3. What are the outputs that should come from the solution to the problem?
4. Can the outputs be determined from the inputs? In other words, do I have enough information to solve the problem?
5. How should I label the important pieces of data that are a part of the problem.

#### An Example:
> Write a function that takes two numbers and returns their sum.

1. implement addition of two input numbers
2. Numbers. BUT are they within the bounds of the language (ie really large numbers)? Integers? Decimals? Are the inputs always two numbers OR can people input more or fewer numbers to add?
3. Should it be a float? An Integer? A String if it's a large number?
4. Yes, but lots of questions!
5. We have a result to return maybe called `sum`, function name `add`, and parameters for the the function: `num1`, `num2`

### 2. Explore Concrete Examples

Coming up with examples can help you understand the problem better. These examples also provide sanity checks that your solution works how it should, like for testing.

When you think about User Stories or Unit Tests are used to give these concrete examples to devs IRL.

- Start with simple examples: the easiest use cases
- Progress to more complex examples
- Explore examples with empty inputs
- Explore examples with invalid inputs

#### An Example
> Write a function which takes in a string and returns counts of each character in the string

1. Simple Examples:
    - `'aaaa'` = `{ a: 4 }`
    - `'hello'` = `{ h: 1, e: 1, l: 2, o: 1 }`
      - What if the letters aren't in there? Should we have `{ b: 0 }`?
2. More complex examples?
    - `'my phone number is 18348257'`
    - `'Hello hi'`
      - What about capital letters? Should the result be `{ H: 1, h: 1 }` or `{ h: 2 }` or `{ H: 2 }`?
3. If it's empty, what do we return?
4. If it's not a string (object, number, etc.)?

### 3. Break It Down

Explicitly write out the steps you need to take. This forces you to think about the code you'll write before you write it, ,and helps you catch any linering conceptal issues or misunderstandings before you dive in.

Let's keep the last example going here. As a reminder, our problem is:
> Write a function which takes in a string and returns counts of each character in the string

```js
charCount(str){
  // loop over string
    // gonna need to lower case string
    // for each character,
      // if the char is a number/letter and is key in object, add one to count
      // if not but is a number/letter, add it and set it to one
      // if the character is something else (space, period, etc.), don't do anything.
  // return an object with keys that are lowercase alphanumeric characters in the string
}
```

### 4. Solve or Simplify

If you can't solve the problem, then try to solve a simpler problem. You want to have something to show for yourself. This can be handled by...
- Finding the core difficulty in what you're trying to do
- Temporarily ignore that difficulty
- Write a simplified solution
- Then incorporate that difficulty back in

Let's keep the last example going here. As a reminder, our problem is:
> Write a function which takes in a string and returns counts of each character in the string

If I struggled with creating a loop, for example, then a good place to start would be working with a single character, inserting it into the object until a pattern is identified.


### 5. Look Back and Refactor

If you get through all of the code for your problem, look back on your code and ask:
- Can you check the result?
- Can you derive the result differently?
- Can you understand it at a glance?
- Can you use the result or method for some other problem?
- Can you improve the performance of your solution?
- Can you think of other ways to refactor?
- How have other people solved this problem?


## Vocabulary
- **Algorithm**: A process or a set of steps to accomplish a certain task.


#### [Back to Home](../../README.md)