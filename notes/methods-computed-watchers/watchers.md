# Watchers

* Each component has a watcher instance
* Properties touched by the watcher during the render are registered as dependencies
* When the setter is triggered, it lets the watcher know & causes the component to re-render

* Calculations in the virtual DOM are relatively cheap => we want to do as many calculations there as possible before bringing it over to the DOM itself
* Vue works off a Vue Model premise

* getters & setters for propertoes


Example:
```
var vm = new Vue({
    el: '#app',
    data() {
        return {
            message: 'This is the initial message',
            otherMessage: 'This is another message'
        }
    }
})
console.log(vm)
vm.thing = 'I as a new thing'
```

```
<div id="app">
    <p> {{ message }}</p>
</div>
```
* The Vue instance is the middleman between the DOM and the business logic
* Watch updates the DOM only if it's required - performing calculations in JS is really performant but accessing the DOM is not. So we have a Virtual DOM which is like a copy, but parsed in JS.
* Only updates the DOM after its done making all of those calculations
* Only update the DOM for things that need to be changed


## Why watchers?
* Good for asynchronous updates & updates/ transitions with data changes

```
new Vue({
    el: '#app',
    data() {
        return {
            // this property here has to have the same name as the property of the watcher in order for it to be picked up
            counter: 0
        }
    },
    watch: {
        counter() {
            console.log('The counter has changed!')
        }
    }
})
```

## Example of using watcher with a fetch

* Can update things on the fly 
* Hooking into reactivity system
```
<div id="app">
// If there's nothing yet here
    <div v=if="beers.length === 0">Loading ...</div>
    <div v-for="beer in beers class="beer-contain>
        <div class="beer-img">
            <img src="beer.img" height"350">
        </div>
        ....
    </div>
</div>
```

```
new Vue({
    el: '#app',
    data() {
        return {
            // bottom has to be a watch property if it is used by watch
           bottom: false,
           beers: []
        }
    },
    watch: {
        bottom(bottom) {
            if (bottom) {
                this.addBeer()
            }
        }
    },
    // a lifecycle hook
    created() {
        window.addEventListener('scroll', () => {
            this.bottom = this.bottomVisible()
        })
        this.addBeer()
    },
    methods: {
        bottomVisible() {
            const scrollv = window.scrollV
            const visible = document.documentElement.clientHeight
             const pageHeight = document.documentElement.scrollHeight
             const bottomOfPage = visible + scrollV >= pageHeight
             return bottomOfPage || pageHeight < visible
        },
        addBeer() {
            axios.get('https://api.punkapi.com/v2/beers/random')
            .then(response => {
                let api = response.data[0];
                let apiInfo = {
                    name : api.name,
                    desc : api.description,
                    img : api.image_url,
                    tips : api.brewers_tips,
                    tagline : api.tagline,
                    food : api.food_pairing,
                };
                this.beers.push(apiInfo);
                if (this.bottomVisible()) {
                    this.addBeer()
                }
            })
        }
    }
})
```

* We also have access to the new value & the old value, e.g.

```
watch: {
    watchedProperty( value, oldValue) {
        // your code here
    }
}
```
* We can transition between the new & old

* We can also gain access to nested values with 'deep'
```
watch: {
    watchedProperty {
        deep: true,
        nestedWatchedProperty (value, oldValue) {
            // your code here
        }
    }
}
```

* SVG & maths => transitioning with these rather than D3 for example

```
<select v-model="selected">
    <option v-for="option in options" v-bind:value="options.value">
    {{ option.text }}
    </option>
</select>
```
* [Greensock](https://greensock.com/) could be useful for modern web animation
* Bars could be automatically 