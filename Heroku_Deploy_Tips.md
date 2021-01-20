# 6 Steps to Deploy MERN project's to the Heroku
### Step 1
```
make your Node.js project and make a "client" Folder and create react inside that folder
```
### Step 2
```javascript
inside "client" folder run :

npm run build
```

### Step 3
```javascript
inside server.js write :

if (process.env.NODE_ENV === "production") {
  app.use(express.static('client/build'));
}
```

### Step 4
```javascript
inside package.json write :

"scripts": {
    "build": "cd client && npm run build",
    "install-client": "cd client && npm install",
    "heroku-postbuild": "npm run install-client && npm run build",
    "start": "node server.js",
    "client": "cd client && npm start"
  },
  "engines": {
    "node": "10.16.3"
  },
}
```

### Step 5
```javascript
add and push everything to github : 

git add .
git commit -m "commit"
git push -u origin master
```

### Step 6
```javascript
deploy it on heroku : 

git push heroku master

```




