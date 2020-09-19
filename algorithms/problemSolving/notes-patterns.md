# Problem Solving Patterns

There is no cure-all, foolproof pattern that will apply to 

## Resources
- []()


## Frequency Counters

This pattern uses objects or sets to collect values/frequencies of values. This can often avoid the need for nexted loops or O(n<sup>2</sup>) operations with arrays/strings.

### Example: Compare Squared Values

> Write a function called same, which accepts two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency of values must be the same.

One "naive" method to do this would be to loop over each value of the first array, square it, search for the index of the matching squared value in the second array, and if we find it, then splice it. If we don't find it, we can return false.

```js
function same(arr, sqArr) {
  // if the arrays are different lengths, then we immediately know it will be false, so check for that first
  if( arr.length !== sqArr.length ) {
    return false;
  }

  for( let i = 0; i < arr.length; i++ ) {
    let squaredIdx = sqArr.indexOf(arr[i] ** 2)
    if( squaredIdx === -1 ) {
      return false;
    }

    sqArr.splice(squaredIdx, 1);
  }
  return true;
}
```
As it stands, this function has an efficiency of O(n<sup>2</sup>), or quadratic time. However, if we think about this in terms of objects, we can improve upon this function. **REMEMBER: two loops are always better than nested loops.**
```js
function same(arr, sqArr) {
  // we can keep the same initial check as the first time.
  if ( arr.length !== sqArr.length ) {
    return false;
  }

  // we can use objects to keep a count of how many times it occurs in that list.
  let counter1 = {};
  let counter2 = {};

  // let's fill our objects (AKA map our values) with the value frequencies.
  for( let val of arr ) {
    counter1[val] = (counter1[val] || 0) + 1;
  }

  for( let val of sqArr ) {
    counter2[val] = (counter2[val] || 0) + 1;
  }

  // now we can compare the objects and their frequency
  for( let key of counter1 ){
    // when we take the key in counter1 and square it, do we find it in counter two? If we DON'T, then we can return false.
    if( !( key ** 2 in counter2 ) ) {
      return false;
    }

    // finally, let's check and see if the value of counter2 at counter1's key squared is the same value of that of counter1 at key. If the values are not the same, then the frequency does not match and we can return false.
    if( counter2[key ** 2] !== counter1[key] ) {
      return false;
    }
  }

  // if we get through all of the key/value pairs of our counter objects without returning false, then all the key values and their frequencies must match, so we can return true.
  return true;
}
```

### Example: Anagrams

> Given two strings, write a function to determine if the second string is an anagram of the first. An anagram is a word, phrase, or name formed by rearranging the letters of another, such as _cinema_, formed from _iceman_. Can assume all lowercase, single word, and no extra characters.

```js
function validAnagram(str, compStr) {
  if ( str.length !== compStr.length ) {
    return false;
  }
  
  let counter = {};
  
  for ( let i = 0; i < str.length; i ++ ) {
    let char = str[i];
    // if letter exists, increment, otherwise set to 1
    counter[char] ? counter[char] += 1 : counter[char] = 1;
  }
    
  for ( let i = 0; i < compStr.length; i++ ) {
    let char = compStr[i];
    // if the character can't be found in the counter or if the value is 0, then return false.
    if (!counter[char]) {
      return false;
    } else {
      // if it is found, then decrement the value at that character.
      counter[char] -= 1;
    }
  }
  
  return true;
}
```

## Multiple Pointers

Creating **pointers** or values that correspond to an index or position and move towards the beginning, end, or middle based on a certain condition. This is a very efficient way for solving problems with minimal space complexity.

## Vocabulary



#### [Back to Home](../../README.md)