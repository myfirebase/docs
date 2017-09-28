
As the name implies, the navigation guards provided by vue-router are primarily used to guard navigations either by redirecting it or canceling it. There are a number of ways to hook into the route navigation process: globally, per-route, or in-component.

!!! warning
    Remember that params or query changes won't trigger enter/leave navigation guards. You can either watch the $route object to react to those changes, or use the beforeRouteUpdate in-component guard, see [vue-router global navigation guards](https://router.vuejs.org/en/advanced/navigation-guards.html).

### Myfirebase global navigation guards.

#### Creating middleware

Myfirebase provides a simple way to create navigations guards or middlewares, you could simply run `myfirebase new:middleware <middleware-name>`. Myfirebase-cli will generate a middleware template for you located in `/src/middlewares/` directory.

The middleware generated might look something like this:

```javascript
/**
 * MiddlewareNmae, you can get access
 * to myfirebase functionalities and vue auth guard via actions.
 * myfirebase => [auth, storage, store]
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

If you want a middleware to run during every route navigation to your application, simply list the middleware function in the `middleware` property of your `/src/middlewares/index.js`.

#### Auth Middleware

Myfirebase comes with an exmaple of auth middleware called AuthMiddleware located in middlewares directory, this will check if the user is signed-in or not, and redirecting users to the login page.

As you may notice, you will find in the **route.js** file a **metadata** called auth, which is assigned to **App** and **UpdateProfile** components.

!!! tip
    Routing [docs](routing.md).

### Auth middleware

```javascript
/**
 * AuthMiddleware, you can get access
 * to myfirebase functionalities and vue auth guard via actions.
 * myfirebase => [auth, storage, store]
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