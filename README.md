# Docker-Node-Application-Sever
Creating a simple Node Application Sever using Docker  

## Overview
This project aims at creating a simple Node-Express application server using Docker

## Part 1: Create Node Application
### Step 1: Create 'package.json'
```javascript
{
  "name": "docker_web_app",
  "version": "1.0.0",
  "description": "Node.js on Docker",
  "author": "Kaustubh Olpadkar <kaustubh.olpadkar@gmail.com>",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.16.1"
  }
}

```

### Step 2: Install dependencies
```terminal
$ npm install
```

### Step 3: Create 'server.js'
```javascript
'use strict';

const express = require('express');

// Constants
const PORT = 8080;
const HOST = '0.0.0.0';

// App
const app = express();
app.get('/', (req, res) => {
  res.send('Hello world\n');
});

app.listen(PORT, HOST);
console.log(`Running on http://${HOST}:${PORT}`);
```


## Part 2: Running Node Application in Docker
### Step 1: Create 'Dockerfile'
```
FROM node:8

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm install --only=production

# Bundle app source
COPY . .

EXPOSE 8080

CMD [ "npm", "start" ]
```

### Step 2: Create '.dockerignore'
```
node_modules
npm-debug.log
```

### Step 3: Build Docker Image
```
$ sudo docker run -p 49160:8080 -d kaustubh/node-web-app
```

### Step 4: 
```
$ sudo docker run -p 49160:8080 -d kaustubh/node-web-app
```

Now our Application Server is running and you can access it through http://localhost:49160 in your browser.
