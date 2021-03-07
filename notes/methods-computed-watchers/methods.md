# Methods, Computed & Watchers
* All different ways of working with the data available to us

* Watchers -> used for special occasions

## Methods
* Are bound to the Vue instance. They are incredibly useful for functions you would like to access in directives.
* Hang a method off a Vue instance


```
<div id="app" :style="{
    backgroundColor: `hsl(${x}, 80%, 50%`}" 
    @mousemove="xCoordinate">
    <p>
     <button @click="increment">+</button>
      <button @click="decrement">-</button>
    </p>
    <p>Pixels across: {{ x }} <p>
</div>
```


```
new Vue({
    el: '#app',
    data() {
        return {
            counter: 0,
            x: 0
        }
    },
    methods: {
        increment() {
            this.counter++;
        },
        decrement() {
            this.counter--;
        },
        xCoordinate(e) {
            this.e = e.clientX;
        }
    }
})
```

* Anytime use methods or computed, need `this.something` -> don't really need to figure out what this actually means
* Methods -> especially useful for if you have 
* Don't need an arrow function for this method because binding data -> can use an arrow function inside of a method
* Don't have to pass in event using Vue -> still offered `e` parameter though on the relevant method
* `hsl` -> really nice for generative colours as it will never fail
* Always executed like a function