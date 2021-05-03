# Mixins

* Could have 2 components which are very similar - share same basic functionality, but there's enough that's different about each of them that you come to crossroads: split into 2 or keep in 1 - but create enough variance with props that can alter each one?
* A mixin allows you to encapsulate one piece of functionality, to use it in different components throughout the application
* If written correctly, pure - don't modify or change things outside of the fns scope
* You will reliably always receive the same value with the same inputs on multiple executions
* Can extract the shared functionality , e.g.

```
const toggle = {
    data() {
        return {
            isShowing: false
        }
    }
}

methods: {
    toggleShow() {
        this.isShowing = !this.isShowing;
    }
}


// consumes here the small fn into the component & reuses them

const Modal = {
    template: `#modal`,
    mixins: [toggle],
    components: {
        appChild: child
    }
}


const Tooltip = {
    template: `#tooltip`,
    mixins: [toggle],
    components: {
        appChild: child
    }
}

```

* Examples: getting dimensions of viewport & component, gathering specific mouse events, base elements of charts
* An example project: https://github.com/paulpflug/vue-mixins


### Merging
* Concept of merging with mixins => by default, mixins will be applied first & the component will be applied second so we can override it as necessary
* The component has the last say
* Mixins have all life cycle events available to them
* If you have multiple then component wins 


### Global mixins
* WARNING: Are applied to every single component
* One use that could make sense could be a plugin, where you have to gain access to everything
* Use case for them is extremely limited & they should be considered with great caution

