#Heroku Page:
https://heroku-bp-v1.herokuapp.com/
# How to deploy to Heroku 
- I should remove everithig related to favicon (into index.html, angular.js)

- Run: `npm install --save express path`
- Changes into `package.json`
- `"scripts": {
    ...
    "start": "node server.js",
    "postinstall": "ng build --prod"
  },
  "engines": {
    "node": "8.11.3",
    "npm": "6.1.0"
  },`

- `node --version
npm --version`
- Move @angular/cli, @angular/compiler-cli, typescripty "@angular-devkit/build-angular": "~0.6.8"__ __ * from `devDependencies` to `dependencias`.
- Create in root a `server.js` with this information:
<code>const path = require('path');
const express = require('express');
const app = express();
// Serve static files
app.use(express.static(__dirname + '/dist/MY_APP_NAME'));
// Send all requests to index.html
app.get('/*', function(req, res) {
  res.sendFile(path.join(__dirname + '/dist/MY_APP_NAME/index.html'));
});
// default Heroku port
app.listen(process.env.PORT || 5000);</code>
Replace MY_APP_NAME with your app name.
- Create Heroku app and first follow the deploy instructions
  
###References
- https://medium.com/@roliver_javier/como-desplegar-tu-aplicacion-de-angular-en-heroku-7b9941b6d39
- https://dev.to/gedgonz/haciendo-deploy-de-una-app-en-angular-a-heroku-16ji