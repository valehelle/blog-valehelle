---
layout: post
title:  "3 mistakes I made when learning React Native"
date:   2018-02-25 06:35:45 +0000
categories: React-Native
---
##### React Native is a great platform for you to target both IOS and Android simultaneously without sacrificing your app performance. However, not all things are perfect. Here are some things that I learn while working on a React Native project.

## 1. Trying to learn React Native and Redux at the same time.
When I first started learning React Native, I made a mistake of learning Redux at the same time. I thought that you cannot do one without the other. This make learning simple things alot more complex than it should. You should start with the basic. Create a project using only React Native. When you are comfortable with it, then you can move to learning Redux.

## 2. Never state the version number.
When importing any library, always include the **version number only**. Never leave it blank or "^" .

```javscript
//This is bad
"redux": "3.6.0",
"redux-logger": "^3.0.1"
```
```javscript
//This is good
"redux": "3.6.0",
"redux-logger": "3.0.1"
```
The reason for this is simple. If you did not put a version number, bundler will always install the latest version. Lets say your original project uses redux version  3.5.0.When you clone from a repository like github, because you did not specify your redux version, bundler will install the latest version. This will make your clone project out of sync with your original one and this can cause issue with some 3rd party library.

## 3. Using Redux for everything.
Redux is a powerful tool. But you should not used it for everything. In my early days of using React Native I store everything in Redux. Including a simple input text field. Not only that this add to the length of code,but it also complex things that was simple. Use Redux only when it makes sense, where that data is needed globally. Otherwise, local variable is just fine.
