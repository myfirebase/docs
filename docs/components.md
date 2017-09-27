Components contain your HTML rendred by your application and houses scripts and stylessheets that belogs to that component located in the `/src/components/` directory.

Myfirebase used VueJs templates components, with single component concept that provide sepation of concerns.

Typicaly, to create a new component you could run `new:component command` in your terminal.

`myfirebase new:component <component-name>`, the Myfirebase-CLI will generate a new component template and put it inside your application `/src/components/<component-name>.vue`.

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
            hello: 'Hello myfirebase'
        }
    }
}

</script>

<style scoped>
/*Stylesheet*/
</style>
```