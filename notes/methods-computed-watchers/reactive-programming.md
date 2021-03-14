# What is reactive programming?

* Reactive programming is programming with asynchronous data streams
* RXJS -> a common library which does fall under this umbrella
* A stream is a sequence of ongoing events ordered in time that offer some hooks with which to observe it, e.g. hover stream -> transitioning state
* When we use reactive premises for building applications, this means it's very easy to update state in reaction to events
* Really ^^ is why we use Vue => Vue is helpful when we are changing & interactive things
* Blog post to read [here](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)


## What is Reactive?
Some examples:
* Angular 1.x -> dirty checking
* Cycle.js & Angular 2 use reactive streams like XStream & Rx.js
* Vue.js, MobX or Ractive.js all use a variation of getters/setters - useful info [here](https://vuejs.org/v2/guide/reactivity.html)
* React is not reactive - it is a pull rather than a push mechanism


* Vue takes the object, walks through its properties & converts them to getter/setters


```
new Vue({
    data: {
        text: 'msg'
    }
})
```
* Vue can't detect property addition or deletion so we create this object to keep track -> we need that object to keep access