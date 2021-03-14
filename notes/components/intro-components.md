# Components

* A collection of elements that are encapsulated into a group that can be accessed through one single element

... for example
```
<div>
<p></p>
<div></div>
<p></p>
<small></small>
</div>
```

can be abstracted into this component & be abstracted out
```
<callout></callout>
```

## Simplest Vue component

// create component that can be accessed
// any added to template can be found here , rather than directly in the Vue instance
```
Vue.component('child', {
    template: <div>hello mr.magoo</div>
})
```

```
new Vue({
    el: "#app"
});
```

## Slightly more complex with props


// reuse a component but slightly change one part of it => this is when props are really helpful
```
Vue.component('child', {
    props: ['text'],
    template: `<div> {{ text }} </div>`
})
```

// dynamically bind to props `:text`
```
<div id="app">
// this text gets passed down from the parent to the child component
    <child :text="message"></child>
</div>
```


```
new Vue({
    el: "#app",
    data() {
        return {
            message: 'hello mr. magoo'
        }
    }
});
```