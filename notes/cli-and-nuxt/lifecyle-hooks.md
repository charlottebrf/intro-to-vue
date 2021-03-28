# Lifecycle hooks

* Provide you a method to trigger something precisely at different junctures of a component's lifecycle
* Components are mounted when we instantiate them, & in turn unmounted, for instance when toggled in `v if /else ` statement

## Examples of hooks
* beforeCreate
* created
* beforeMount
* mounted
* beforeUpdate
* updated
* activated
* deactivated 
* beforeDestroy
* destroyed


## Lifecyle
* These will occur again & again in the same order 



* `beforeCreate()` - observe data & init events
* `created()` - template options & render
* `beforeMount()` - create virtual DOM el & replace `el` with it
* `mounted()`
    * `beforeUpdate()` - virtual DOM rerender & patch
    * `updated()`
    * `activated()` - keep alive component reactivated
    * `deactivated()`
* `beforeDestroy()` - tear down the watchers , child components, event listeners
* `destroyed()`

* Autobind to the instance - to use the component's state
* Shouldn't use an arrow function on a lifecycle method , as it will return a parent instead of giving you a nice binding out of the box
* We are doing everything on entrance: as soon as the component is mounted we can do lots of different things 
