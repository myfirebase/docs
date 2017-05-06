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

 - `/src/component` directory as the name implies, contains alll of your application components files, here wjere you can create new Vue components, according to vuejs, components took **.vue** as extemsion, see [Vuejs Components](https://vuejs.org/v2/guide/components.html).

For sure, you are free to define and organize this directory structure however you like.

#### `/storage`

The Storage Directory contains all of your storage files.

**What is storage??**

Storage is a state management pattern + library for Vue.js applications, Vuex keeps components communicating to each other, see [Vuex](https://vuex.vuejs.org/en/).

#### Public Directory

Public directory contains the main index.html file, this directory also houses all of your application compiled assets files css/js, **these assets will be injected to index.html automatically**

 - index.html *index page*

 - 404.html *NotFound page 404*

 - css *css directory*

 - js *js directory*