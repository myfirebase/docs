By default, Myfirebases structure provides a great starting point for your application. However, you are free to organize your files/directories as you like.

#### Root Directory

The root directory contains **src**, **build**, **config**, **functions** and **public** directories. 

This directory also houses your firebase.json and database.rules.json file.

#### `/src`

Your main code lives here, Where the application core is located, `firebase`, routes, main.js and Vue components, 99% of the time, you'll be working in `src/ `.

 - `/src/assets` directory, where you can write your global sass/scss preprocessor.

 - `/src/firebase` directory, contains firebase SDK classes and config.js file, 

 - `/src/routes` directory, where you can define your application routes, [Vuejs Routes Docs](https://router.vuejs.org/en/). 

 - main.js file where your application core is defined. 

 - `/src/component` directory as the name implies, contains all of your application components files, here where you can create new Vue components, according to vuejs, components took **.vue** as extension, see [Vuejs Components](https://vuejs.org/v2/guide/components.html).

For sure, you are free to define and organize this directory structure however you like.

#### `/functions`

!!! tip "Firebase Cloud functions docs"
    New to firebase?, please see [Firebase Cloud functions docs](https://firebase.google.com/docs/functions/).

In the firebase cloud functions directory,you can write some back-end functions to handle cloud messaging and business logic if necessary and a lot of advanced stuff.

!!! tip "Google Cloud Platform"
    It's become easier to integrate some advanced technologies such as machine learning and image processing with [Google Cloud Platform](https://cloud.google.com) and more.

#### `/storage`

The storage directory contains all of your storage files, using one of Vuejs eco-system, see [Vuex](https://vuex.vuejs.org/en/).

#### `/public`

The public directory contains the main index.html file, it also houses all of your applications compiled assets CSS, JS files and service-workers, **these assets will be auto injected to index.html**

!!! note "service workers"
    Google developers had made some cool articles about the service-worker concept, see [Service Workers: an Introduction](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers).

 - index.html *index page*

 - 404.html *NotFound page 404*

 - css *css directory*

 - js *js directory*

 - service-worker.js

 - firebase-messaging-sw.js

 - manifest.json

#### `/build`

Apparently, you may not want to touch anything right here, this directory contains all the **build** files managed by node.js unless you want to specify some of your additional configuration such as development server port, service-workers or even changing web pack configuration, then you may proceed.

#### `/config`

Where the development and the production mode configuration are located.

#### `/static`

Where static files are located, images and icons are used as a static assets in your applications.

#### `/tests`

Where your application tests are located, by default Myfirebase comes with eslint and karma for unit testing, you are free to integrate other libraries and plugins such as [night watch](http://nightwatchjs.org/) e2e.
