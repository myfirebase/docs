Myfirebase is using Vuex which is a simple scalable state managment system compatible with vuejs, all myfirebase states are located in `/storage` directory.

Storage directory houses `store.js`, `myfirebase-auth` and `myfirebase-storage`.

!!! tip
    It's recommended to check vuex [docs](https://vuex.vuejs.org)

**Authentication** and **Cloud Storage** states are seperated from each other and splited up into modules under a namespace.

!!! Warning
    You're free to add new states and mutations, but you're not allowed to change the default states/mutations because they're used by **Myfirebase plugin**.


