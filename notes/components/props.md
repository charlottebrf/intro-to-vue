# Props
* Passing down from the parent to the child 
* Always an array, always strings
`props: ['text']`
* Props are intended for one way communication
* Can think of it like: the component holds a variable that is waiting to be filled out by whatever the parent sends down to it

// dynamically props text can be used to point to one message or another
```
Vue.component('child', {
    props: ['text'],
    template: `<div> {{ text }} </div>`
})
```

// dynamically bind to props `:text`
```
<div id="app">
child component
    <child :text="message"></child>
    <child :text="otherMessage"></child>
</div>
```


```
new Vue({
    el: "#app",
    data() {
        return {
            message: 'hello mr. magoo'
            otherMessage: 'hello there!!!'
        }
    }
});
```

## Types & validation

* Can define what types the prop should be
```
props: {
    text: [String, Number]
}
```

* One step further can add in a default in case nothing is shown 
```
Vue.component('child', {
    props: {
        text: {
            type: String,
            required: true,
            default: 'Hello mr.magoo'
        }
    }
    template: `<div> {{ text }} </div>`
})
```
* Validation 
* Will get a warning if you use the wrong type -> validate props

### Objects & arrays
Note: objects & arrays need their defaults to be returned from a function

```
text: {
    type: Object,
    default: function() {
        return {message: 'hello mr magoo' }
    }
}

```
* Should include a default as a function

* Don't necessarily need to pass the data in props to the child

* Not using the state of the parent
`<child count="I"></child>`

vs
* Using the state of the parent
`<child :count="count"></child>`

* We use `v-bind` or `:` to dynamically bind props to data on the parent *

* Each component instance has its own isolated scope data must be a function - [isolated components](https://vuejs.org/v2/guide/components.html#data-Must-Be-a-Function)
* Data must be a function!
* Get into the 


* camelCasing will be converted
`props: ['booleanValue]`

* In HTML it will be kebab-case:
`checkbox :boolean-value="booleanValue"></checkbox`