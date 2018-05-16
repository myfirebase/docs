Myfirebase ships with the [vue-material](http://vuematerial.io) to build well-crafted apps with Material Design and Vue 2, that makes working with material-design and JavaScript a joy.

By default, vue-material is already integrated into this project, you can specify your favorite theme color in `/src/main.js`

```javascript
...

// Default
Vue.material.registerTheme('default', {
    primary: 'blue',
    accent: 'red',
    warn: 'orange',
    background: 'white'
})

// Login
Vue.material.registerTheme('login', {
    primary: 'indigo',
    accent: 'blue',
    warn: 'black',
    background: 'white'
})

...
```

#### Define global styles

As you may know, Myfrebase has a default SASS/SCSS file located in `/src/assets/sass/app.scss`, this file contains all vue-material SASS dependencies, you're free to choose whatever you want to work with, this file is compiled down via webpack automatically and injected into `index.html` while running `npm run build` or `npm run dev`.

```css

/* app.scss */

/* Fonts */

@import url(https://fonts.googleapis.com/icon?family=Material+Icons);

/* Variables */


/* @import "variables"; */


/*VueMaterial css*/

@import '~vue-material/dist/components/mdAvatar/index.css';
@import '~vue-material/dist/components/mdBackdrop/index.css';
@import '~vue-material/dist/components/mdButton/index.css';
@import '~vue-material/dist/components/mdCard/index.css';
@import '~vue-material/dist/components/mdCore/index.css';
@import '~vue-material/dist/components/mdIcon/index.css';
@import '~vue-material/dist/components/mdLayout/index.css';
@import '~vue-material/dist/components/mdList/index.css';
@import '~vue-material/dist/components/mdMenu/index.css';
@import '~vue-material/dist/components/mdSelect/index.css';
@import '~vue-material/dist/components/mdSidenav/index.css';
@import '~vue-material/dist/components/mdSpeedDial/index.css';
@import '~vue-material/dist/components/mdSubheader/index.css';
@import '~vue-material/dist/components/mdTabs/index.css';
@import '~vue-material/dist/components/mdToolbar/index.css';
@import '~vue-material/dist/components/mdWhiteframe/index.css';
@import '~vue-material/dist/components/mdSwitch/index.css';
@import '~vue-material/dist/components/mdInputContainer/index.css';
@import '~vue-material/dist/components/mdSnackbar/index.css';
@import '~vue-material/dist/components/mdDialog/index.css';
@import '~vue-material/dist/components/mdTable/index.css';
@import '~vue-material/dist/components/mdSpinner/index.css';
@import '~vue-material/dist/components/mdFile/index.css';

/*Global css*/

.container {
    margin-top: 15px;
}

.overlay {
    z-index: 9000;
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgba(0, 0, 0, 0.7);
    transition: opacity 500ms;
    visibility: visible;
    opacity: 1;
}

.flex-spinner {
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: center;
}
```

`.flex-spinner` and `.overlay` class will be triggered globally in your application so you can start using them in every single component you create.

!!! tip
    Not familiar with material design? you're free to choose whatever type of CSS frameworks you want to work with such as bootstrap or Bulma.