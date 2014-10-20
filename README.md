#Sample RESTful Web App with Node.js, Express, and MongoDB

## Deloy in CF
* Clone [this repo](https://github.com/gfoligna/node-tutorial-2-restful-app.git) repo to a directory called “nodejs-mongodb-sample” (git clone https://github.com/gfoligna/node-tutorial-2-restful-app.git nodejs-mongodb-sample)
  * _cd nodejs-mongodb-sample_
* Create a mongodb service using the CF CLI using the name you picked in the manifest (in this case __mongodb-sample__ is set by default)
* Push
* Browse the URL in port 80 to test if it works (http://nodejs-mongodb-sample.YOURDOMAIN)
* Try adding a few users to test if the DB is working properly
