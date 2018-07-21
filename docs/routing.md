Myfirebase is using Vuejs routes system, all routes are located in `/src/routes/routes.js`.

!!! tip 
    It's recommended to check the vue-router [docs](https://router.vuejs.org/en/).

#### Vue-router and Myfirebase

By default, Myfirebase has some default routes already defined in `routes.js` file.

- Layout.vue: which is the default layout of the application.

- Welcome.vue: which is a default welcome component.

- Login.vue: which is responsible for authenticating users (register/login/logout) using firebase authentication.

- UpdateProfile.vue: which is responsible for updating user profile (email/password) and user avatar using firebase cloud storage.

- App.vue: which is the default component to manipulate the firebase database.

- Firestore.vue: which is the default component to use the cloud firestore.

```javascript

import Landing from '@/components/Landing'
import Welcome from '@/components/Welcome'
import Login from '@/components/auth/Login'
import UpdateProfile from '@/components/auth/UpdateProfile'
import App from '@/components/App'
import Firestore from "@/components/Firestore"

import Vue from 'vue'

const routes = [{
        path: '/',
        component: Landing,
        children: [{
                path: '/',
                component: Welcome,
                name: 'Welcome'
            },
            {
                path: '/login',
                component: Login,
                name: 'login'
            },
            {
                path: '/update-profile',
                component: UpdateProfile,
                name: 'Profile Update',
                meta: {
                    auth: true
                }
            },
            {
                path: '/app',
                component: App,
                name: 'Main app',
                meta: {
                    auth: true
                }
            },
            {
                path: '/firestore',
                component: Firestore.
                name: 'firestore',
                meta: {
                    auth: true
                }
            }
        ]
    },
    {
        path: '*',
        components: NotFound
    }
]


export default routes;
```