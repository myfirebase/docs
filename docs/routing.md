Myfirebase is using Vuejs routes system, all routes are located in `/src/routes/routes.js`.

!!! tip 
    It's recommended to check the vue-router [docs](https://router.vuejs.org/en/)

#### Vue-router and Myfirebase

By default, Myfirebase has some default routes already defined in `routes.js` file.

- Landing component: which is the parent of all other components.

- Welcome component: which is a default landing component.

- Login component: which is responsible for authenticating users (register/login/logout) using firebase authentication.

- UpdateProfile: which is responsible for updating user profile (email/password) and user avatar using firebase cloud storage.

- App component: which is a default app example to create/read data to the firebase database.

```javascript

import Landing from '@/components/Landing'
import Welcome from '@/components/Welcome'
import Login from '@/components/auth/Login'
import UpdateProfile from '@/components/auth/UpdateProfile'
import App from '@/components/App'

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