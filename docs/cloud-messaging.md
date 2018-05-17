Firebase cloud messaging is a powerful tool that provides a simple mechanism to deliver push notifications easily to your Android, IOS or web applications.

!!! tip "Firebase Cloud Messaging"
    Please check FCM [docs](https://firebase.google.com/docs/cloud-messaging/)

### FCM and Myfirebase

As you may know, FCM javascript API allows you receive notification messages among browsers that provide service worker support.

This includes the following browsers:

- Chrome: 50+
- Firefox: 44+
- Opera Mobile: 37+

!!! warning
    The FCM SDK is supported only in pages served over HTTPS, due to its use of service workers which are available only on HTTPS sites, Thanks to firebase hosting which provide free hosting for your web application served under HTTPS, Sending messages from the Firebase console is not supported.

To get started with FCM in your project, you have to add your `messagingSenderId` in `firebase-messaging-sw.js` which is located in public directory.

```javascript

// Give permission to the service worker.
// Note that you can only use Firebase Messaging here, other Firebase libraries
// are not available in the service worker.
importScripts('https://www.gstatic.com/firebasejs/3.9.0/firebase-app.js');
importScripts('https://www.gstatic.com/firebasejs/3.9.0/firebase-messaging.js');

// Initialize the Firebase app into the service worker with the senderID.
firebase.initializeApp({
    'messagingSenderId': 'Your-sender-id'
});
const messaging = firebase.messaging();

// Retreive an instance of Firebase Messaging so we can handle the background
// messages.
messaging.setBackgroundMessageHandler(function(payload) {
    // Customize notification here
});

```

This service worker will handle notification messages even in the background when the users browser is not opened the .
