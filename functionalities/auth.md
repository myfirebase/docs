## Authentication

> Before you begin, please check the [firebase auth docs](https://firebase.google.com/docs/auth/web/start).

How hard it is to integrate **Firebase auth** to your web project especially when you try to structure and orginize firebase auth globally to be used through all **Vue components**.

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
        mounted() {
            // retrieve username.
            this.userName = this.$auth.user().displayName
            // retrieve user email.
            this.userEmail = this.$auth.user().email
        },
        data() {
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
        mounted() {
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

You can update profile pricture usign `updateProfilePicture(object)` method, this will update the default firebase user **profileURL**.

> Before you start updating profile picture, make sure that you have uploaded that picture to firebase storage, and get photoURL, see [Upload a file with Myfirebase]().

Syntax : `$auth.updateProfilePicture(object)`

##### Example

```html
<script>
    export default {
        mounted () {

        },
        data () {
            return {
                // link to profile photo
                picture: 'https://link-to-photo.test/profile.png'
            }
        },
        methods:{
            // update profile picture
            updateProfilePicture() {
                this.$auth.updateProfilePicture({
                    // picture link
                    ref: this.picture,
                    result: () => {
                        //updated
                    },
                    error: (error) => {
                        console.log(error.message)
                    }
                })
            }
        }
    }
<script>
```
<hr>

#### Auth state

Syntax : `$auth.state(object)`

Consider it just like a auth middleware where you can check if the user is signed in or not, you can also redirect user to an other component if he doesn't signed in.

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
        mounted() {
            // Check if the user signed in with redirection. 
            this.$auth.state({
                forward: '',
                redirect: '/login',
                then: (user) => {
                    this.userName = user.displayName 
                },
                catch: (error) => {
                    console.log(error.message)
                }
            })
        },
        data() {
            return {
                userName: ''
            }
        }
    }
</script>
```

<hr>

#### Auth check

Just like **auth state** but without redirection.

Syntax : `$auth.check(object)`

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
        mounted() {
            // Check if the user signed in without redirection. 
            this.$auth.check({
                then: (user) => {
                    this.signed = true
                    this.userName = user.displayName 
                },
                catch: (error) => {
                    console.log(error.message)
                }
            })
        },
        data() {
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

Synax : `$auth.registerWithEmailAndPassword(object)`

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
        mounted() {
            // Check if the user signed in with redirection. 
            this.$auth.state({
                forward: '/app',
                redirect: '/login',
                then: (user) => {
                    //
                },
                catch: (error) => {
                    console.log(error.message)
                }
            })
        },
        data() {
            return {
                email: '',
                password: '',
            }
        },
        methods: {
            registerWithEmailAndPassword(){
                // register user with email and password
                this.$auth.registerWithEmailAndPassword({
                    email: this.email,
                    password: this.password,
                    result: (user) => {
                        console.log("User Email : " + user.email)
                    },
                    error: (error) => {
                        console.log(error.message)
                    }
                });
            }
        }
    }
</script>
```
<hr>

#### SignIn with email and password

To signin a user with email and passowrd.

Syntax : `$auth.loginWithEmailAndPassword(object)`

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
        mounted() {
            // Check if the user signed in with redirection. 
            this.$auth.state({
                forward: '/app',
                redirect: '/login',
                then: (user) => {
                    //
                },
                catch: (error) => {
                    console.log(error.message)
                }
            })
        },
        data() {
            return {
                email: '',
                password: '',
            }
        },
        methods: {
            loginWithEmailAndPassword() {
                // login with email and password
                this.$auth.loginWithEmailAndPassword({
                    email: this.email,
                    password: this.password,
                    result: (user) => {
                        console.log("User Email : " + user.email)
                    },
                    error: (error) => {
                        console.log(error.message)
                    }
                });
            }
        }
    }
</script>
```

<hr>

#### SignIn with google

let your users authenticate with Firebase using their **Google accounts**.

Syntax : `$auth.signInWithGoogle(object)`

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
        mounted() {
            // Check if the user signed in with redirection. 
            this.$auth.state({
                forward: '/app',
                redirect: '/login',
                then: (user) => {
                    //
                },
                catch: (error) => {
                    console.log(error.message)
                }
            })
        },
        data() {
            return {
            }
        },
        methods: {
            signInWithGoogle() {
                // SignIn with google
                this.$auth.signInWithGoogle({
                    result: (user) => {
                        // This gives you a Google Access Token. You can use it to access the Google API.
                        // The signed-in user info.
                    },
                    error: (error) => {
                        console.log(error.message)
                    }
                });
            }
        }
    }
</script>
```

<hr>

#### SignIn with Facebook

To let your users authenticate with Firebase using their **Facebook Accounts**.

Syntax : `$auth.signInWithFacebook(object)`

<hr>

#### SignIn with Twitter

To let your users authenticate with Firebase using their **Twitter Accounts**.

Syntax : `$auth.signInWithTwitter(object)`

<hr>

#### SignIn with Github

To let your users authenticate with Firebase using their **Github Accounts**.

Syntax : `$auth.signInWithGithub(object)`

<hr>

#### Logout

To sign out a user, call `logout`.

Syntax : `$auth.logout()`
