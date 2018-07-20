---
layout: post
title:  "How to create NodeJS Script"
date:   2018-07-18 06:35:45 +0000
categories: React-Native
---
#### 1. Create a NodeJS package.
A NodeJS package is basically a folder that contains you package.json and also your js script. You can generate it by running
`npm init`
When you run this command it will ask you a bunch a question and will generate a package.json file for you.
```
package name: (node) demo
version: (1.0.0) 
description: this is a demo
entry point: (index.js) 
test command: 
git repository: 
keywords: 
author: hazmi irfan
license: (ISC) 
About to write to /Users/hazmiirfan/Desktop/Node/package.json:

{
  "name": "demo",
  "version": "1.0.0",
  "description": "this is a demo",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "hazmi irfan",
  "license": "ISC"
}


Is this OK? (yes) yes
```

#### 2. Create Javascript file
Next you need to create your own Javascript file. For this demo I will create a Javascript "index.js" file to print "Hello World"
`console.log('Hello World')`
We can then call it using
```
Hazmis-MacBook-Pro:Node hazmiirfan$ node index.js
Hello World
```
#### 3. Convert the Javascipt file into a NodeJS command-line script

Similar as other shell script, we want to make our JavaScript file executable by the locally installed node program. We do that adding a shebang character sequence at the very top of our JavaScript file that look as follow:
```
#!/usr/bin/env node
console.log('Hello World')
```
We are basically telling *nix systems that when running this script, the interpreter should be `/usr/bin/env` node which looks up for the locally-installed node executable.
Now if we try to run the program using `./index.js` you will get an error
```
Hazmis-MacBook-Pro:Node hazmiirfan$ ./index.js
-bash: ./index.js: Permission denied
```
This is because the file is only allowed to be read by a user. We need it to have execute permission as well.
```
Hazmis-MacBook-Pro:Node hazmiirfan$ ls -l
total 16
-rw-r--r--  1 hazmiirfan  staff   47 Jul 18 10:32 index.js
-rw-r--r--  1 hazmiirfan  staff  225 Jul 18 10:23 package.json
```
We can change it by running
`chmod +x index.js`
We can then see that now our file have execution permission for our user as well.
```
Hazmis-MacBook-Pro:Node hazmiirfan$ chmod +x index.js 
Hazmis-MacBook-Pro:Node hazmiirfan$ ls -l
total 16
-rwxr-xr-x  1 hazmiirfan  staff   47 Jul 18 10:32 index.js
-rw-r--r--  1 hazmiirfan  staff  225 Jul 18 10:23 package.json
```
If we run the `./index.js` again we got
```
Hazmis-MacBook-Pro:Node hazmiirfan$ ./index.js
Hello World
```
#### 3. Map a command-line script to a command name
So far, we converted a Javascript file into a NodeJS command-line script file. However, we want to give it a more meaningful name that does not need to be the name of the NodeJS command-line script file. For that, we have to map our command-line script by configuring our package.json
We can do this by adding 
```
"bin"{
    "demo": "./index.js"
}
```
to the package.json file.
Now our package.json file will look like this
```
{
  "name": "demo",
  "version": "1.0.0",
  "description": "this is a demo",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "bin"{
    "demo": "./index.js"
  },
  "author": "hazmi irfan",
  "license": "ISC"
}
```
Next we can run `npm link` which allows us to run our Javscript file using `demo`
```
Hazmis-MacBook-Pro:Node hazmiirfan$ npm link
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN demo@1.0.0 No repository field.

up to date in 10.201s
/usr/local/bin/demo -> /usr/local/lib/node_modules/demo/index.js
/usr/local/lib/node_modules/demo -> /Users/hazmiirfan/Desktop/Node
Hazmis-MacBook-Pro:Node hazmiirfan$ demo
Hello World
````
Congrats! now we can play with our NodeJS command-line script locally before `npm publish`‘ing them.

#### Note on how to use other package on your script.
If you want to use other people package on your script,
all you need to do is insert
```
dependencies:{
    "npm-name": "npm-version"
}
```
into your package.json file.

