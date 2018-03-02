---
layout: post
title:  "5 Things you should now before learning React Native"
date:   2018-01-25 06:35:45 +0000
categories: React-Native
---
#### React Native is a great platform for you to target both IOS and Android simultaneously without sacrificing your app performance. However, not all things are perfect. Here are some things that you should know before learning React Native.

## 1. No folder structure
There is no folder structure in React Native. On android when you create a project,there is at least a basic folder structure for you to start with. This might be okay for veteran programmer as they already have their own folder structure that they like but can be difficult for newcomers.


## 2. No navigation
On android navigation is automatically handled. If I want to move to a new screen, I just start the Intent.

```java                 
Intent intent = new Intent(_instance, LoginActivity.class);
startActivity(intent);
````

However in React Native, you need to import your own 3rd party navigation library and also learn how to use them correctly.


## 3. Javascript
React Native is coded in javascript. For a web developer this might be a positive but for Android developer this may take some time to get used to.

## 4. 3rd party library
You need to import many 3rd party library before your app is actually usable. If there is a new version of React Native but not supported in one of your library, then you are stuck on using the old version of React Native.

## 5. Error message is not obvious.
React Native although error loudly, is sometime not clear with its error message. This can frustrate newcomers.