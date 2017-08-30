## Checking out the project structure

By default, Myfireabse Application structure provides a great starting point for your application, For sure, you are free to organize your files/directories however you like.

#### Root Directory

The root directory contains **src**, **build**, **config**, **functions** and **public** directories. 

This directory also houses your firebase.json and database.rules.json file.

#### `/src`

Your main code lives here, Where the application core is located, `firebase`, routes, main.js and Vue components, 99% of the time, you'll be working in `src/ `.

 - `/src/assets` directory, where you can write your global sass/scss preprocessor.

 - `/src/firebase` directory, contains firebase SDK class and config.js file, 

 - `/src/routes` directory, where you can define your application routes, [Vuejs Routes Docs](https://router.vuejs.org/en/). 

 - main.js file where your application core is defined. 

 - `/src/component` directory as the name implies, contains all of your application components files, here wjere you can create new Vue components, according to vuejs, components took **.vue** as extemsion, see [Vuejs Components](https://vuejs.org/v2/guide/components.html).

For sure, you are free to define and organize this directory structure however you like.

#### `/functions`

!!! tip "Firebase Cloud functions docs"
    New to firebase?, please see [Firebase Cloud functions docs](https://firebase.google.com/docs/functions/).

Firebase cloud functions directory, where the cloud functions are located, in this directory you could write some back-end functions to handle cloud messaging and business logic if necessary and alot of advanced stufs. 

!!! tip "Google Cloud Platform"
    It's become more easier to integrate some advanced stufs such like machine learning and image processing with [Google Cloud Platform](https://cloud.google.com).

#### `/storage`

The storage directory contains all of your storage files.

**What is storage??**

Storage contains state management pattern + library for Vue.js applications files, Thanks to Vuex for keeping components communicating to each other, see [Vuex](https://vuex.vuejs.org/en/).

#### `/public`

Public directory contains the main index.html file, this directory also houses all of your application compiled assets files css/js and service-workers as well, **these assets will be injected to index.html automatically**

!!! note "service workers"
    Google developers had made some cool articles about service, see [Service Workers: an Introduction](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers).

 - index.html *index page*

 - 404.html *NotFound page 404*

 - css *css directory*

 - js *js directory*

 - service-worker.js

 - firebase-messaging-sw.js

 - manifest.json

#### `/build`

Apparently you may not touch anything right here, this directory contains all the **build** files managed by node.js

#### `/config`

Where development and production mode configuration is located.

#### `/static`

Where static files are located, images and icons are used as a static assets into your applications and provide them to support Progressive web applications.

#### `/tests`

Where your application tests are located, by defualt Myfirebase comes with eslint and karma for unit testing, you are free to integrate others libraries and plugins such like [night watch](http://nightwatchjs.org/) e2e.