# Templates

* Vue.js uses HTML based template syntax to bind the Vue instance to the DOM, very useful for components
* Templates are optional, can also write render functions with optional JSX support
* Start with template strings (only useful for small cases), then to script, then to single file templates in the next section 


## Simple template (not too useful)

```
var app = new Vue({
    el: '#app',
    // this template is a string
    template: '<div>hello mr.magoo</div>'
});
```
//the template gets put inside of this div
```
<div id="app"></div>
```

## Components
* Abstract pieces away
```
<header></header>
    <aside>
        <sidebar-item v-for="item in items"></sidebar-item>
    </aside>
    <main>
        <blogpost v-for="post in posts"></blogpost>
    </main>
<footer></footer>
```