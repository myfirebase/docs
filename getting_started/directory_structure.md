## Checking out the project structure

By default, Myfireabse Application structure provides a great starting point for your application, For sure, you are free to organize your files/directories however you like.

#### Root Directory

The root directory contains **src**, **build**, **config**, **functions** and **public** directories. 

This directory also houses your firebase.json and database.rules.json file.

#### `/src`

Your main code lives here, Where the application core is located, `firebase`, routes, main.js and Vue components, 99% of the time, you'll be working in `src/ `.

 - assets directory, where you can write your global sass/scss preprocessor.

 - `firebase` directory, contains firebase SDK class and config.js file, 

 - routes directory, where you can define your application routes, [Vuejs Routes Docs](https://router.vuejs.org/en/). 

 - main.js file where your application core is defined. 

#### Component Directory

Component Directory,as the name implies, contains all of your application's components files, here where you can create new Vue components, according to Vuejs, components took **.vue** as extensions. See [Vuejs Components](https://vuejs.org/v2/guide/components.html).

This directory contains all of defaults components such like:

 - **Login.vue** : Login/register component (Auth Example).

 - **App.vue** : An example of real time database.

 - **UpdateProfile.vue** : An example of updating user profile (Auth/storage Example).

 - **Welcome.vue / Landing.vue** : Default app index component.

 - **Navbar.vue** : Default Navbar component.

For sure, you are free to define and organize this directory structure however you like.

#### `/storage`

The Storage Directory contains all of your storage files.

**What is storage??**

Storage is a state management pattern + library for Vue.js applications, Vuex keeps components communicating to each other, see [Vuex](https://vuex.vuejs.org/en/).

#### Public Directory

Public directory contains the main index.html file, this directory also houses all of your application's compiled assets files css/js.

 - index.html *index page*

 - 404.html *NotFound page 404*

 - css *css directory*

 - js *js directory*