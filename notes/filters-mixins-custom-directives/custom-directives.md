# Custom directives


```
Vue.directive('tack', {
    bind(el, binding, vnode) {
        el.style.position = "fixed
    }
});
```

### Directive deep dive
* `v-example` => will instantiate a directive, but doesn't accept any arguments. Without passing a value, this would not be very flexible - but you could still hang some piece of functionality off the DOM element
* `v-example="value"` =>  pass a value into the directive & the directive figures out what to do based off that value.
* `v-example="string"` - this will let you use a string as an expression
* `v-example:arg="value"` => allows us to pass an argument to the directive. In the example below we're binding to a class & we'd style it with an object stored separately.
* `v-example:arg.modifier="value` => this allows us to use a modififer. The example below allows us to call `preventDefault()` on the click event.

### Different hooks available
* Unbind
* Bind => insertion into the DOM, often this is the one you can use
* Inserted => element is inserted
* Updated => element is updated (access to vnode & oldvnode)
* Component updated => children are updated
* Can use this lib to attach to the events http://imakewebthings.com/waypoints/
