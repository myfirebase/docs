
As the name implies, the navigation guards provided by vue-router are primarily used to guard navigation either by redirecting it or canceling it. There are a number of ways to hook into the route navigation process: globally, per-route, or in-component.

!!! warning
    Remember that params or query changes won't trigger enter/leave navigation guards. You can either watch the $route object to react to those changes or use the beforeRouteUpdate in-component guard, see [vue-router global navigation guards](https://router.vuejs.org/en/advanced/navigation-guards.html).

### Myfirebase global navigation guards.

#### Creating middleware

Myfirebase provides a simple way to create navigations guards or middlewares, you could simply run `myfirebase new:middleware <middleware-name>`. Myfirebase-cli will generate a middleware template for you located in the `/src/middlewares/` directory.

Typically, The middleware generated might look something like this:

```javascript
/**
 * MiddlewareNmae, you can get access
 * to myfirebase functionalities and vue auth guard via actions.
 * myfirebase => [auth, storage, store, firestore]
 * actions => [to, from, next()]
 * 
 * @param {object} myfirebase 
 * @param {object} actions 
 */
const MiddlewareName = (myfirebase, actions) => {
    // you can get access to the database via myfirebase.store.
    // Example
    // var e = myfirebase.store.state.database.ref.child('/foo')
    // console.log(e)
    // actions.next()
}

export default MiddlewareName
```
#### Registring middlware

If you want a middleware to run during every route navigation to your application, simply list the middleware function in the `middlewares` array of your `/src/middlewares/index.js`.

```javascript
/**
 * Here where you can register your middlewares
 * you could simply do that by adding them to the middlewares array.
 */

// import AuthMiddleware.
import AuthMiddleware from './auth'

// import your new middleware.
import MiddlewareName from './MiddlewareName'

// register AuthMiddleware and MiddlewareName.
const middlewares = [AuthMiddleware, MiddlewareName]

export default middlewares
```

#### Auth Middleware

Myfirebase comes with an example called AuthMiddleware located in middlewares directory, this will check if the user is signed-in or not, and redirect users to the login page.

As you may notice, you will find in the **route.js** file a **metadata** called auth, which is assigned to **App** and **UpdateProfile** components.

!!! tip
    Routing [docs](routing.md).
 
```javascript
/**
 * AuthMiddleware, you can get access
 * to myfirebase functionalities and vue auth guard via actions.
 * myfirebase => [auth, storage, store, firestore]
 * actions => [to, from, next()]
 * 
 * @param {object} myfirebase 
 * @param {object} actions 
 */
const AuthMiddleware = (myfirebase, actions) => {
    if (actions.to.matched.some(record => record.meta.auth)) {
        myfirebase.auth.check({
            then: () => {
                actions.next()
            },
            catch: () => {
                actions.next({ path: '/login' })
            }
        })
    } else {
        actions.next()
    }
}

export default AuthMiddleware
```

### Myfirebase and Per-Route Guard

You can define beforeEnter guards directly on a route's configuration object, and also retrieve Firebase Auth, database, and storage by importing Vue:

```javascript

// Components.
import Welcome from '@/components/Welcome'
import Example from '@/components/Example'

//Vue.
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
                path: '/example'
                component: Example,
                name: 'example',
                // Pre-Route Guard.
                beforeEnter: (to, from, next) => {
                    // retrieve firebase Auth
                    var auth = Vue.auth;
                    if(auth.user().email === "example@mail.com"){
                        next()
                    }else{
                        next({path: '/login'})
                    }
                } 
            }
        ]
    },
    {
        path: '*',
        components: NotFound
    }
]
```