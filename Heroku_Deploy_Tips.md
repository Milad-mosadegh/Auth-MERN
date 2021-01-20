# All Steps to Deploy MERN project's to the Heroku
### Step 1
```
make your node.js project and make a "client" Folder on root folder and create react inside that folder
```

# After finish the Project make a github repo and push everything there, make an new app inside heroku

 ### Step 2
```javascript
 // To connect your github project to heroku 
heroku git:remote -a "heroku app name"
```

### Step 3
```javascript
// inside "client" folder run :
npm run build
```

### Step 4
```javascript
// inside server.js after "cookieParser" write :

if (process.env.NODE_ENV === "production") {
  app.use(express.static('client/build'));
}
app.use(express.static(path.join(__dirname, 'client', 'build')));


//BEFOR app.listen() should write : 
app.get("*", (req, res) => {
  res.sendFile(path.join(__dirname, 'client', 'build', 'index.html'))
})

```

### Step 5
```javascript
// inside package.json write :

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

### Step 6
```javascript
// add and push everything to github : 

git add .
git commit -m "commit"
git push -u origin master
```

### Step 7
```javascript
// BEFOR DEPLOY 
heroku local // to test application before deploying

// deploy it on heroku : 
git push heroku master

```




