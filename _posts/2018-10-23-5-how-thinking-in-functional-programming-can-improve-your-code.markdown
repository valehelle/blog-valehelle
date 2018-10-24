---
layout: post
title:  "How thinking in Functional Programming can improve your code."
date:   2018-10-23 06:35:45 +0000
categories: Functional-Programming
---
Functional Programming(FP) is a programming paradigm. You are likely more familiar with a more popular programming paradigm which is Object Oriented Programming(OOP).

FP relies on a few concepts:

1. Every function should be a pure function.

2. Avoid shared state.

3. Avoid mutable data.

4. Declarative rather than Imperative.

5. Uses recursion instead of loop.

6. High Order Functions.

Because of this concept, FP code tends to be more concise, more predictable, and easier to test than object oriented code .

Although they are functional language like Elixer, Erlang and Elm, most language that we uses such as Java, Javascript, C# are object oriented rather than functional. But, we can still use some of the concept of FP to benefit our own code. Mainly shared state and immutable data.

I'm going to share an example of my real code that I wrote at work. I have change it to make it easier to understand but the basic structure is the same.

The purpose of this function is given a number:
1. If it is lesser than 5, the `actualNum` would show "Less than 5".

2. If it is greater than 5, it would show "Greater than 5".

3. If it is greater than 5 and `maxNum` it would show "Greater than 5 and 
maxNum".

4. If it is equal to 5 it would show "Equal to 5".

5. `displayNum` would show "" if number is greater than 5 and `maxNum`,  otherwise it would show the same value as `actualNum`.

Here is the code:
```javascript
let maxNum = 10
function getNumber(num){
      let isGreater = false
      let actualNum = ""
      let displayNum = ""
 
      if (num) {
        if (num < 5) {
            actualNum = "Less than 5"
        } else if (num > 5)
        {
          if (num > maxNum) {
            isGreater = true
            actualNum = "Greater than 5 and maxNum"
          } else {
            actualNum = "Greater than 5"
          }
        } else if (num === 5) {
            actualNum = "Equal to 5"
        }
 
        if (isGreater) {
            displayNum = ""
        } else {
            displayNum = actualNum
        }
      }
      console.log(`actualNum: ${actualNum} \ndisplayNum: ${displayNum}`)
}
```
From here, it is hard for you to know which variable `actualNum` and `displayNum` depends on. Declaring the variable at the top with a default value and then changing the value of it as it goes along the code is the normal way I code. Since this is how I learned during my University days. However, if this code grows, tracking each variable and its value would get more hard and complex.

So now let's try applying some of the FP concepts.


## Immutable Data
Immutable data simply means that an object will never change it's value. In Java we can use `Final` but in Javascript, they are no equivalent without using external library. For now we are going to use `const` and treat it like an Immutable object. Since we can't change the variable value, we can no longer declare it at the top. The only way to overcome this is to declare a variable and have a function return the value that we want.

```javascript
const maxNum = 10
 
function getActualNum(num){
    if (num < 5) {
        return "Less than 5"
    } else if (num > 5)
    {
        if (num > maxNum) {
          return "Greater than 5 and maxNum"
        } else {
          return "Greater than 5"
        }
    } else if (num === 5) {
        return "Equal to 5"
    }
}
 
function isGreaterThan(num){
      if (num > 5 && num > maxNum) {
        return true
      } else {
        return false
      }
}
 
function getDisplayNum(isTerminatedFlow, actualNum){
    if (isTerminatedFlow) {
        return ""
      } else {
        return actualNum
      }
}
 
function getNumber(num){
    if (num) {
       
      const actualNum = getActualNum(num)
      const isGreater = isGreaterThan(num)
      const displayNum = getDisplayNum(isGreater, actualNum)
 
 
      console.log(`actualNum: ${actualNum} \ndisplayNum: ${displayNum}`)
    }
}
```
So from here you can see that the code instantly become more readable. A new person reading the code would have no trouble understanding what each function actually do. But we can still improve on this.

## Avoid Shared State

Shared state is a state which is shared between more than one function or more than one data-structure. For the code above, `maxNum` is a global variable which can be accessed by any function. So we need to remove this and pass it to only the function that needed it.

```javascript
function getActualNum(num, maxNum){
    if (num < 5) {
        return "Less than 5"
    } else if (num > 5)
    {
        if (num > maxNum) {
          return "Greater than 5 and maxNum"
        } else {
          return "Greater than 5"
        }
    } else if (num === 5) {
        return "Equal to 5"
    }
}
 
function isGreaterThan(num, maxNum){
      if (num > 5 && num > maxNum) {
        return true
      } else {
        return false
      }
}
 
function getDisplayNum(isGreater, actualNum){
    if (isGreater) {
        return ""
      } else {
        return actualNum
      }
}
 
function getNumber(num){
    if (num) {
      const maxNum = 10
      const actualNum = getActualNum(num, maxNum)
      const isGreater = isGreaterThan(num, maxNum)
      const displayNum = getDisplayNum(isGreater, actualNum)
 
 
      console.log(`actualNum: ${actualNum} \ndisplayNum: ${displayNum}`)
    }
}
```

That's it. By having the concept that a variable can never change its value and a function would not use anything outside of its own, the code is not only more readable, but the outcome is also more predictable. It is also easier to test since the function value can be mock easily.

From `getNumber` function you know `actualNum` and `isGreater` depends on `num` and `maxNum` variable while `displayNum` depends on `isGreater` and `actualNum` variable. Yes, you will be forced to write more code but the outcome is a more readable, testable and predictable code.

They are other concept we can apply such as pure function but for this example I can only apply those 2.
