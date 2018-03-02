---
layout: post
title:  "My React Native folder structure"
date:   2018-03-01 03:55:00 +0000
categories: React-Native
---
##### For React Native beginner it can be hard to structure project. The lack of documentation from Facebook also did not help. Below you can find my folder structure. 

```
project
│   index.js
│   ios    
│   android
└───app
│   │
│   └───actions
│   │
│   └───components
│   │
│   └───config
│   │
│   └───containers
│   │
│   └───helpers
│   │
│   └───reducers
```

## 1. app
This is the parent folder for React Native code.

## 2. actions
Folder to store all of the actions.

## 3. components
All dumb component like buttons and text field are placed here.

## 4. config
The configuration folder of the app like router and database.

## 5. containers
All smart component are placed here. Generally this consist of screen. Example login screen and feed screen.

## 6. helpers
This is a place to store all the functions that can be used across the app.

## 7. reducers
Folder to store all of the reducers.

##### [I have created a project on github as a reference](https://github.com/valehelle/kangar-rn-template]). I am planning to explain more in depth about the structure in the future. 