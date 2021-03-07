## Computed Properties
* Computed properties are calculations that will be cached & will only update when needed
* Highly performant but use with understanding
* Could be something useful if there's a fetch for example


```
<div id="app">
    <h3>Your name: <input v-model.lazy="userData"/></h3>
    <h2 v-if="userData">Initial entry: {{ userData }}</h2>
    <h2 v-if="userData">Computed Value: {{ greeting }}</h2>
    
</div>
```

```
new Vue({
    el: '#app',
    data() {
        return {
            userData: ''
        }
    },
    computed: {
        greeting() {
            return 'You are a monster', {this.userData}
        },
    }
})
```
* Using `greeting` as a property - used as though it is a piece of data related to the Vue instance
* Different view of the same data - doesn't mutate the original
* Using our computed property in place of the data, we now have a different view of the data


#### COMPUTED  
* Runs only when a dependency has changed
* Cached
* Should be used as a property, in place of data
* By default getter only, but you can define a setter



#### METHODS 
* Runs whenever an update occurs
* Not cached
* Typically involved from `v-on/@`, but flexible
* Getter / Setter

```
    methods: {
        sortLowest() {
            this.ratingInfo.sort((a, b) => a.rating > b.rating ? 1 : -1);
        },
    }
```


````

computed: {
    filteredFilms() {
        let filter = new RegExp(this.filterTest, `1`)
        return this.ratingsInfo.filter(el => el.title.match(filter))
    }
}
```


```
    <tr v-for="entry in ratingsInfo">
        <td v-for="key in column">
        {{ entry[key]}}
        </td>
    </tr>
```