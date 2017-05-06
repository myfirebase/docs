
##Installation

#### Prerequisites

1. **NPM** is the recommended installation method when building large scale applications with **Myfirebase**.

   If this is the first time you want to give **npm** a shot, don't worry, we got exactly what you need.

   - [How to Install Node.js and NPM on Windows](http://blog.teamtreehouse.com/install-node-js-npm-windows)

   - [How to Install Node.js and NPM on a Mac](http://blog.teamtreehouse.com/install-node-js-npm-mac)

   - [How to Install Node.js and NPM on a Linux](http://blog.teamtreehouse.com/install-node-js-npm-linux)

2. **Firebase command line interface**, `npm install -g firebase-tools`

#### Installing Myfirebase

```shell
# Clone the repository
git clone https://github.com/myfirebase/myfirebase

# Change directory
cd myfirebase

# Install dependencies
npm install

# Sign in using your Google account
firebase login

# Initialize firebase project
firebase init
```

#### Run dev server

```shell
# Run the server
npm run dev
```

#### Production


```shell
# Production
npm run build
```

#### Deploy your project

```shell
# Deploy project
firebase deploy
```

#### Congratulations

You've installed **Myfirebase** correctly.

Now let's dive right in to this framework directory to see what's going on, [Directory Structure](directory_structure.md).