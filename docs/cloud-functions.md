!!! tip "Firebase Cloud functions docs"
    Please check the firebase cloud functions [docs](https://firebase.google.com/docs/functions/).

Basically, Myfirebase comes with `/functions` directory where you could define and organize your functions and deploy them efficiently.

Functions directory houses index.js, package.json and node modules, so you can organize and structure this directory however you like.

## Getting started

```shell
# move to functions directory.
$ cd functions

# install dependencies.
$ npm install
```

By default, index.js comes with an example of sending a push notification after the `onWrite` event.

```js
// index.js

// require firebase-functions.
var functions = require('firebase-functions');
// require firebase-admin.
var admin = require('firebase-admin')
// initialize firebase app.
admin.initializeApp(functions.config().firebase);
// export sendMessageNotification as a function. 
exports.sendMessageNotification = functions.database.ref('data/{messageID}').onWrite(event => {
    if (event.data.previous.exists()) {
        return;
    }
    // get data.
    admin.database().ref('data').child(event.params.messageID).once('value').then(function(snap) {
        // retrieve meassage
        var messageData = snap.val();
        // retrieve token
        var topic = messageData.token;
        // define payload.
        var payload = {
            notification: {
                title: "You got a new Message",
                body: messageData.data,
                icon: 'https://cdn4.iconfinder.com/data/icons/google-i-o-2016/512/google_firebase-2-128.png'
            }
        };
        // send push notification.
        admin.messaging().sendToDevice(topic, payload)
            .then(function(response) {
                console.log("Successfully sent message:", response);
            })
            .catch(function(error) {
                console.log("Error sending message:", error);
            });
    });
});
```

As you can see it's easy to write functions with firebase cloud functions.

!!! info "Firebase cloud messaging" 
    This example of sending push notification requires registering a service-worker through client site (browser) which is already defined in this project, check the following link [Cloud Messaging](cloud-messaging.md).