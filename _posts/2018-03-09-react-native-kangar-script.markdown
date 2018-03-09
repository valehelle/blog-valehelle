---
layout: post
title:  "My React Native Script Kangar"
date:   2018-03-09 03:00:00 +0000
categories: React-Native
---
##### Coding in React Native can be time consuming. Because there is a lot of boilerplate code that you need to write each time. This is especially true when you use Redux as well. I created a script to help you generate a React Native project with Redux. Its highly opiniated and have a strict project structure that you have to follow. I hope this script can help some beginners.

## 1. Install

```
npm install kangar
npm link kangar
```


## 2. Create project
```
kangar init <project_name>
```

This will create a React Native project with this structure

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
To run the project just use the normal React Native command.
```
react-native run-android
react-native run-ios
```

## 3. Create action
```
kangar generate action <action_name>
```
## 4. Create reducer
```
kangar generate reducer <reducer_name>
```
## 5. Create container
```
kangar generate action <container_name>
```