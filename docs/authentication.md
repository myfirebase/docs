
!!! tip 
    It's recommended to take a look at the firebase authentication docs, please check the following link[firebase auth docs](https://firebase.google.com/docs/auth/web/start).

How hard it is to integrate **Firebase auth** to your web project especially when you try to structure and organize firebase auth globally to be used through all **Vue components**.

Thanks to **Myfirebase auth system** which makes firebase auth easier to be managed using **Vuex**, the fireabse auth is injected and triggered at beginning of the Vue instance.

<hr>

#### Auth instance

Syntax : `$auth`

`$auth` is a global auth instance which called through Vue component.

##### Example

```html
<template>
    <div class = "container">
        <!-- display result -->
        User Name : {{userName}}
        Email :     {{userEmail}}
    </div>
<template>

<script>
    export default {
        mounted () {
            // retrieve username.
            this.userName = this.$auth.user().displayName
            // retrieve user email.
            this.userEmail = this.$auth.user().email
        },
        data () {
            return {
                userName: ''
            }
        }
    }
</script>
```

Basically `$auth` instance is your key to get access and manage **firebase auth**.

<hr>

#### Get Firebase Auth Module

To retrieve firebase auth module.

Syntax : `$auth.getAuth()`

<hr>

#### Get current user

You can get the current signed in user by calling global auth instance.

Syntax : `$auth.getUser()`

##### Example

```html
<script>
    export default {
        mounted () {
            // get current user
            let user = this.$auth.getUser()
            // get email
            console.log(user.email)
            // get username
            console.log(user.displayName)
        }
    }
</script>
```

<hr>

#### Update Profile Picture

You can update profile avatar usign `updateProfilePicture(object)` method, this will update the default firebase user **profileURL**.

!!! tip
    Before you start updating profile picture, make sure that you have uploaded that picture to firebase storage, and get photoURL, see [Upload a file with Myfirebase]().

Syntax : `$auth.updateProfilePicture(String)`
Return : `Promise`

##### Example

```html
<script>
    export default {
        data () {
            return {
                // link to profile photo
                picture: 'https://link-to-photo.test/profile.png'
            }
        },
        methods: {
            // update profile picture
            updateProfilePicture () {
                this.$auth.updateProfilePicture(this.picture)
                .then(() => {
                    // updated
                }).catch((error) => {
                    // error
                })
            }
        }
    }
</script>
```
<hr>

#### Auth state

Syntax : `$auth.state(String, String)`
Return : `Promise`

Consider it just like an auth middleware where you can check if the user is signed in or not, you can also redirect the user to another component if he doesn't sign in.

##### Example

```html
<template>
    <div class = "container">
        <!-- display result -->
        User Name : {{userName}}
    </div>
<template>

<script>
    export default {
        mounted () {
            // Check if the user signed in with redirection.
            this.$auth.state('/app', '/login')
            .then((user) => {
                this.userName = user.displayName
            }).catch(error => {
                console.log(error.message)
            })
        },
        data () {
            return {
                userName: ''
            }
        }
    }
</script>
```

<hr>

#### Auth check

It's the same as **auth state** but without redirection.

Syntax : `$auth.check()`
Return : `Promise`

##### Example

```html
<template>
    <ul class="nav navbar-nav navbar-right">
        <li v-if = "signed" class="">
            <a href="#">{{userName}}</a>
            <ul class="dropdown-menu">
                <li>>Logout</a></li>
            </ul>
        </li>
    </ul>
<template>

<script>
    export default {
        mounted () {
            // Check if the user signed in without redirection. 
            this.$auth.check()
            .then((user) => {
                this.signed = true
                this.userName = user.displayName
            }).catch((error) => {
                console.log(error.message)
            })
        },
        data () {
            return {
                userName: '',
                signed: false,
            }
        }
    }
</script>
```

<hr>

#### Signup with email and password

To register a new user with email and password.

Synax : `$auth.registerWithEmailAndPassword()`
Return : `Promise`

##### Example

```html
<template>
    <div class = "register">
        <input type="text" v-mode="email">
        <input type="password" v-model="password">
        <button @click="register"></button>
    </div>
<template>

<script>
    export default {
        mounted () {
            // Check if the user signed in with redirection. 
            this.$auth.state('/app', '/login')
            .then((user) => {
                // user signed-in
            }).catch(error => {
                console.log(error.message)
            })
        },
        data () {
            return {
                email: '',
                password: '',
            }
        },
        methods: {
            registerWithEmailAndPassword () {
                this.$auth.registerWithEmailAndPassword(this.eamil, this.password)
                .then((user) => {
                    console.log(`User Email : ${user.email}`)
                }).catch(error => {
                    // error
                })
            }
        }
    }
</script>
```
<hr>

#### SignIn with email and password

To sign in a user with email and passowrd.

Syntax : `$auth.loginWithEmailAndPassword(String, String)`
Return : `Promise`

##### Example

```html
<template>
    <div class = "register">
        <input type="text" v-mode="email">
        <input type="password" v-model="password">
        <button @click="loginWithEmailAndPassword"></button>
    </div>
<template>

<script>
    export default {
        mounted () {
            // Check if the user signed in with redirection. 
            this.$auth.state('/app', '/login')
            .then((user) => {
                // user signed-in
            }).catch(error => {
                console.log(error.message)
            })
        },
        data () {
            return {
                email: '',
                password: '',
            }
        },
        methods: {
            loginWithEmailAndPassword () {
                // login with email and password
                this.$auth.loginWithEmailAndPassword(this.email, this.password)
                .then((user) => {
                    console.log(user.email)
                }).catch((error) => {
                    console.log(error.message)
                })
            }
        }
    }
</script>
```

<hr>

#### SignIn with google

Allow the users to authenticate to Firebase using their **Google accounts**.

Syntax : `$auth.signInWithGoogle()`
Return : `Promise`

##### Example

```html
<template>
    <div class = "register">
        <h3>SignIn using google account</h3>
        <button @click="signInWithGoogle">Using google</button>
    </div>
<template>

<script>
    export default {
        mounted () {
            // Check if the user signed in with redirection. 
            this.$auth.state('/app', '/login')
            .then((user) => {
                // user signed-in
            }).catch(error => {
                console.log(error.message)
            })
        },
        data () {
            return {
            }
        },
        methods: {
            signInWithGoogle () {
                // SignIn with google
                this.$auth.signInWithGoogle()
                .then(user => {
                    console.log(user.email)
                }).catch(error => {
                    console.log(error.message)
                })
            }
        }
    }
</script>
```

<hr>

#### SignIn with Facebook

Allow the users to authenticate to Firebase using their **Facebook Accounts**.

Syntax : `$auth.signInWithFacebook()`
Return : `Promise`

<hr>

#### SignIn with Twitter

Allow the users to authenticate to Firebase using their **Twitter Accounts**.

Syntax : `$auth.signInWithTwitter()`
Return : `Promise`

<hr>

#### SignIn with Github

Allow the users to authenticate to Firebase using their **Github Accounts**.

Syntax : `$auth.signInWithGithub()`
Return : `Promise`

<hr>

#### SignOut

To sign out a user, call `logout`.

Syntax : `$auth.logout()`
Return : `Promise`