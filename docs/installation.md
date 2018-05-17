#### Prerequisites

1. **NPM** is the recommended installation method when building large-scale applications with **Myfirebase**.

    If this is the first time you are trying **npm** , don't worry, we'll guide you every step of the way.

    - [How to Install Node.js and NPM on Windows](http://blog.teamtreehouse.com/install-node-js-npm-windows)

    - [How to Install Node.js and NPM on a Mac](http://blog.teamtreehouse.com/install-node-js-npm-mac)

    - [How to Install Node.js and NPM on a Linux](http://blog.teamtreehouse.com/install-node-js-npm-linux)

2. **Firebase command line interface**, `npm install -g firebase-tools`

3. **Myfirebase-cli**, `npm install -g myfirebase-cli`

#### Installing Myfirebase

- Create a new Myfirebase project via myfirebase-cli. 

```shell
# Create new project with myfirebase-cli
$ myfirebase new:project my-project

# Change directory
$ cd my-project

# Install dependencies
$ npm install
```

- Create a new project through the [Firebase Console](https://console.firebase.google.com).

!!! info
    After creating a new Google Firebase project, copy and paste the configuration information into your project, `/src/firebase/config.js`. You can get your configuration information by clicking on "Add Firebase to your web app" on the Overview page. 

- Login to your Google account.. 

```shell
# Sign in using your Google account
$ firebase login

# Initialize firebase project
$ firebase init
```

- Launch your app.

```shell
# Run the server
$ npm run dev
```

#### Congratulations

!!! success "Congratulations"
    You've now installed **Myfirebase** correctly, now let's dive into the framework directory structure to see what's going under the hood, [Directory Structure](directory-structure.md).

#### Production

```shell
# Production
$ npm run build
```

#### Deploy your project

```shell
# Deploy project
$ firebase deploy
```
