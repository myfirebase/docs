#### Prerequisites

1. **NPM** is the recommended installation method when building large scale applications with **Myfirebase**.

    If this is the first time you want to give **npm** a shot, don't worry, we got exactly what you need.

    - [How to Install Node.js and NPM on Windows](http://blog.teamtreehouse.com/install-node-js-npm-windows)

    - [How to Install Node.js and NPM on a Mac](http://blog.teamtreehouse.com/install-node-js-npm-mac)

    - [How to Install Node.js and NPM on a Linux](http://blog.teamtreehouse.com/install-node-js-npm-linux)

2. **Firebase command line interface**, `npm install -g firebase-tools`

3. **Myfirebase-cli**, `npm install -g myfirebase-cli`

#### Installing Myfirebase

- Create new Myfirebase project via myfirebase-cli. 

```shell
# Create new project with myfirebase-cli
$ myfirebase my-project

# Change directory
$ cd my-project

# Install dependencies
$ npm install
```

- Create a new project through firebase [console](https://console.firebase.google.com).

!!! info
    After creating a new firbase project, copy and past the config object in you project, `/src/firebase/config.js` 

- Login with your google account. 

```shell
# Sign in using your Google account
$ firebase login

# Initialize firebase project
$ firebase init
```

- Run dev server.

```shell
# Run the server
$ npm run dev
```

#### Congratulations

!!! success "Congratulations"
    You've installed **Myfirebase** correctly, now let's dive right in to this framework directory to see what's going on, [Directory Structure](directory-structure.md).

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