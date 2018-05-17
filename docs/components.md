A little advanced, components are custom elements that Vue compiler would attach specified behaviors too. They contain your HTML, scripts, and stylesheets at the same time all in one file.

They are located in the `/src/components/` directory.

To create a new component you need to run `new:component command` in your terminal.

`myfirebase new:component <component-name>`, the Myfirebase-CLI will generate a new component and place it inside your components directory `/src/components/<component-name>.vue`.

A simple component might look something like this:

```html
<template>
    <div class="container">
        {{hello}}
    </div>
</template>


<script>
export default {
    mounted() {
        console.log("Component mounted . . . ")
    },
    data() {
        return {
            hello: 'Hello Myfirebase'
        }
    }
}

</script>

<style scoped>
    /** My Styles **/
</style>
```
