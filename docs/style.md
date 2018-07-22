Myfirebase ships with the [Vuetify](https://vuetifyjs.com) to build well-crafted apps with Material Design and Vue 2, that makes working with material-design and JavaScript a joy.

#### Define global styles

As you may know, Myfrebase has a default SASS/SCSS file located in `/src/assets/sass/app.scss`, this file contains all **Vuetify** SASS dependencies, you're free to choose whatever you want to work with, this file is compiled down via webpack automatically and injected into `index.html` while running `npm run build` or `npm run dev`.

```css
/* Fonts */

@import url(https://fonts.googleapis.com/icon?family=Material+Icons);

/* Variables */


/* @import "variables"; */


/* Vuetify css*/

@import '~vuetify/dist/vuetify.css';

/*Global css*/

.push-down {
    margin-top: 15px;
}

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