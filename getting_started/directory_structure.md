### Directory Structure

By default, Myfireabse Application structure provides a great starting point for your application, For sure, you are free to organize your files/directories however you like.

#### App Directory

Where the application core is located, `firebase`, routes.js, main.js.

 - `firebase` directory contains firebase SDK class and config.js file, 
    
    config file handle firebase SDK config API tokens, database link, auth domain.

 - routes.js file where you can define your application routes, [Vuejs Routes Docs](https://router.vuejs.org/en/). 

 - main.js file where your application core is defined. 

#### Component Directory

Component Directory contains your application components, here where you can create new Vue components, components take **.vue** as extensions. See [Vuejs Components](https://vuejs.org/v2/guide/components.html).

This directory contains defaults components like:

 - **Login.vue** : Login/register component (Auth Example).

 - **App.vue** : An example of real time database.

 - **UpdateProfile.vue** : An example of updating user profile (Auth/storage Example).

 - **Welcome.vue / Landing.vue** : Default app index component.

 - **Navbar.vue** : Default Navbar component.

For sure, you are free to define and organize your components structure however you like.

#### Storage Directory

The Storage Directory contains storage files.

**What is storage??**

Storage is a state management pattern + library for Vue.js applications, Vuex keeps components communicating to each other, see [Vuex](https://vuex.vuejs.org/en/)

#### Public Directory

. . . . . . .