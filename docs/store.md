Myfirebase is using Vuex which is a simple scalable state management system compatible with Vuejs, all of Myfirebase states are located in `/storage` directory.

Storage directory houses `store.js`, `myfirebase-auth` and `myfirebase-storage`.

!!! tip
    It's recommended to check Vuex [docs](https://vuex.vuejs.org)

**Authentication** and **Cloud Storage** states are seperated from each other and splited up into modules under a namespace.

!!! Warning
    You're free to add new states and mutations, but you're not allowed to change the default states/mutations such as **Myfirebase-auth** and **Myfirebase-storage** because they're used by the **Myfirebase plugin**.


