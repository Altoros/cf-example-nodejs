# Overview 

This is a very simple RESTful Web App developed using Node.js, Express and MongoDB.
Our motivation is to provide a step-by-step Cloud Foundry Node.js deployment example

## Requirements
* Cloud Foundry Command Line Interface
Install the latest version from https://github.com/cloudfoundry/cli/releases
* Cloud Foundry PaaS account
We'll use Pivotal Public PaaS. You can get a free trial account in https://run.pivotal.io

## Deloy in CF
* Clone this repo and move it into it
```
$ git clone <repo url>
$ cd <repo directory>
```

* Login into CF
```
$ cf login -a api.run.pivotal.io -u username -p password
```

* Create application requirements/resources
Take a look at the manifest.yml file. You see that there is a 'service' dependency.
```
  services:
  - mongodb-sample
```

In order to run this app, you'll need a DB. Create a free-plan based DB with the CLI
```
$ cf create-service mongolab sandbox mongodb-sample
```

* Deploy ('push' in terms of CF)
Given that you have a 'manifest.yml' file, you don't need anything else.
```
$ cf push
```

You'll start receiving logs such as:
```
12:39 PM $ cf push
Using manifest file /Users/manu/cf/demo-apps/node/cf-example-nodejs/manifest.yml

Creating app altoros-cf-example-nodejs in org Altoros / space demo as mgarciap+cf2@gmail.com...
OK

Creating route altoros-cf-example-nodejs.cfapps.io...
OK

Binding altoros-cf-example-nodejs.cfapps.io to altoros-cf-example-nodejs...
OK

Uploading altoros-cf-example-nodejs...
Uploading app files from: /Users/manu/cf/demo-apps/node/cf-example-nodejs
Uploading 14.5K, 18 files
OK
Binding service mongodb-sample to app altoros-cf-example-nodejs in org Altoros / space demo as mgarciap+cf2@gmail.com...
OK

Starting app altoros-cf-example-nodejs in org Altoros / space demo as mgarciap+cf2@gmail.com...
OK
-------> Buildpack version 1.0.4
Use locally cached dependencies where possible
       See https://devcenter.heroku.com/articles/nodejs-support
-----> Defaulting to latest stable node: 0.10.32
-----> Downloading and installing node
-----> Installing dependencies
       npm WARN deprecated static-favicon@1.0.2: use serve-favicon module
       > kerberos@0.0.4 install /tmp/staged/app/node_modules/mongodb/node_modules/kerberos
       > (node-gyp rebuild 2> builderror.log) || (exit 0)
       make: Entering directory `/tmp/staged/app/node_modules/mongodb/node_modules/kerberos/build'
         SOLINK_MODULE(target) Release/obj.target/kerberos.node
         SOLINK_MODULE(target) Release/obj.target/kerberos.node: Finished
         COPY Release/kerberos.node
       make: Leaving directory `/tmp/staged/app/node_modules/mongodb/node_modules/kerberos/build'
       > kerberos@0.0.3 install /tmp/staged/app/node_modules/mongoskin/node_modules/mongodb/node_modules/kerberos
       > (node-gyp rebuild 2> builderror.log) || (exit 0)
       make: Entering directory `/tmp/staged/app/node_modules/mongoskin/node_modules/mongodb/node_modules/kerberos/build'
         SOLINK_MODULE(target) Release/obj.target/kerberos.node
         SOLINK_MODULE(target) Release/obj.target/kerberos.node: Finished
         COPY Release/kerberos.node
       make: Leaving directory `/tmp/staged/app/node_modules/mongoskin/node_modules/mongodb/node_modules/kerberos/build'
       > kerberos@0.0.4 install /tmp/staged/app/node_modules/mongoose/node_modules/mongodb/node_modules/kerberos
       > (node-gyp rebuild 2> builderror.log) || (exit 0)
       make: Entering directory `/tmp/staged/app/node_modules/mongoose/node_modules/mongodb/node_modules/kerberos/build'
         SOLINK_MODULE(target) Release/obj.target/kerberos.node
         SOLINK_MODULE(target) Release/obj.target/kerberos.node: Finished
         COPY Release/kerberos.node
       make: Leaving directory `/tmp/staged/app/node_modules/mongoose/node_modules/mongodb/node_modules/kerberos/build'
       > bson@0.2.15 install /tmp/staged/app/node_modules/mongodb/node_modules/bson
       > (node-gyp rebuild 2> builderror.log) || (exit 0)
       make: Entering directory `/tmp/staged/app/node_modules/mongodb/node_modules/bson/build'
         CXX(target) Release/obj.target/bson/ext/bson.o
         SOLINK_MODULE(target) Release/obj.target/bson.node
         SOLINK_MODULE(target) Release/obj.target/bson.node: Finished
         COPY Release/bson.node
       make: Leaving directory `/tmp/staged/app/node_modules/mongodb/node_modules/bson/build'
       > bson@0.2.8 install /tmp/staged/app/node_modules/mongoskin/node_modules/mongodb/node_modules/bson
       > (node-gyp rebuild 2> builderror.log) || (exit 0)
         SOLINK_MODULE(target) Release/obj.target/bson.node: Finished
         COPY Release/bson.node
       > bson@0.2.15 install /tmp/staged/app/node_modules/mongoose/node_modules/mongodb/node_modules/bson
       make: Entering directory `/tmp/staged/app/node_modules/mongoose/node_modules/mongodb/node_modules/bson/build'
         CXX(target) Release/obj.target/bson/ext/bson.o
         SOLINK_MODULE(target) Release/obj.target/bson.node
         SOLINK_MODULE(target) Release/obj.target/bson.node: Finished
         COPY Release/bson.node
       make: Leaving directory `/tmp/staged/app/node_modules/mongoose/node_modules/mongodb/node_modules/bson/build'
       debug@0.7.4 node_modules/debug
       static-favicon@1.0.2 node_modules/static-favicon
       morgan@1.0.1 node_modules/morgan
       └── bytes@0.3.0
       cookie-parser@1.0.1 node_modules/cookie-parser
       ├── cookie-signature@1.0.3
       └── cookie@0.1.0
       body-parser@1.0.2 node_modules/body-parser
       ├── qs@0.6.6
       ├── raw-body@1.1.7 (bytes@1.0.0, string_decoder@0.10.31)
       └── type-is@1.1.0 (mime@1.2.11)
       express@4.0.0 node_modules/express
       ├── methods@0.1.0
       ├── parseurl@1.0.1
       ├── utils-merge@1.0.0
       ├── merge-descriptors@0.0.2
       ├── cookie-signature@1.0.3
       ├── escape-html@1.0.1
       ├── qs@0.6.6
       ├── range-parser@1.0.0
       ├── fresh@0.2.2
       ├── buffer-crc32@0.2.1
       ├── cookie@0.1.0
       ├── path-to-regexp@0.1.2
       ├── type-is@1.0.0 (mime@1.2.11)
       ├── serve-static@1.0.1 (send@0.1.4)
       ├── accepts@1.0.0 (negotiator@0.3.0, mime@1.2.11)
       └── send@0.2.0 (mime@1.2.11)
       jade@1.7.0 node_modules/jade
       ├── character-parser@1.2.0
       ├── commander@2.1.0
       ├── void-elements@1.0.0
       ├── mkdirp@0.5.0 (minimist@0.0.8)
       ├── transformers@2.1.0 (promise@2.0.0, css@1.0.8, uglify-js@2.2.5)
       ├── constantinople@2.0.1 (uglify-js@2.4.15)
       ├── monocle@1.1.51 (readdirp@0.2.5)
       └── with@3.0.1 (uglify-js@2.4.15)
       cfenv@1.0.0 node_modules/cfenv
       ├── ports@1.1.0
       ├── underscore@1.7.0
       └── js-yaml@3.2.2 (esprima@1.0.4, argparse@0.1.15)
       mongodb@1.4.19 node_modules/mongodb
       ├── readable-stream@1.0.33-1 (isarray@0.0.1, string_decoder@0.10.31, inherits@2.0.1, core-util-is@1.0.1)
       ├── kerberos@0.0.4
       └── bson@0.2.15 (nan@1.3.0)
       mongoskin@1.4.4 node_modules/mongoskin
       └── mongodb@1.4.4 (kerberos@0.0.3, bson@0.2.8)
       mongoose@3.8.18 node_modules/mongoose
       ├── regexp-clone@0.0.1
       ├── muri@0.3.1
       ├── sliced@0.0.5
       ├── hooks@0.2.1
       ├── mpath@0.1.1
       ├── mpromise@0.4.3
       ├── mquery@0.8.0
       ├── ms@0.1.0
       └── mongodb@1.4.12 (readable-stream@1.0.33-1, kerberos@0.0.4, bson@0.2.15)
-----> Caching node_modules directory for future builds
-----> Cleaning up node-gyp and npm artifacts
-----> No Procfile found; Adding npm start to new Procfile
-----> Building runtime environment

-----> Uploading droplet (9.7M)

1 of 1 instances running

App started

Showing health and status for app altoros-cf-example-nodejs in org Altoros / space demo as mgarciap+cf2@gmail.com...
OK

requested state: started
instances: 1/1
usage: 256M x 1 instances
urls: altoros-cf-example-nodejs.cfapps.io

     state     since                    cpu    memory          disk   
#0   running   2014-10-24 12:40:38 PM   0.0%   53.8M of 256M   52M of 1G  
```

* Go to the app URL (in this case: http://altoros-cf-example-nodejs.cfapps.io) and try adding a few users to test if the DB is working properly
