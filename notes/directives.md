# Directives
* Always pre-pended with `v-` , e.g `v-text`, `v-html`, `v-else`, `v-for`
* More on vue direcives [here](https://011.vuejs.org/guide/directives.html)
* Essentially, a directive is some special token in the markup that tells the library to do something to a DOM element
* There are also custom directives 
* `v-for` -> loops through set of values

```
<div id="app">
    <ul>
        <li v-for="num in 5>
            {{ num }}
        </li>
    </ul>
</div>
```

* 'v-model' -> creates a relationship between the data in the instance/ component & a form input. So you can dynamically update values.

```
    new Vue({
        el: "#app"
        data() {
            return {
                message: 'This is a good place to type things'
            }
        }
    })

```
* Suggest always write `data` as a function & then return that rather than a literal object

```
    <div id="app">
        <h3>Type here:</h3>
        <textarea v-model="message" class="message rows="5" maxlength="72/>
        <br>
        <p class="booktext"> {{ message }} </p>
    </div>
```
* Immediately creates relationship & outputs text in input field
* Can make really nice interactions very quickly

`Vue.config.devtools = true`

```
new Vue({
    el: '#app',
    data: {
        checkedNames: []
    }
})
```

* Example using `v-model` -> but in a bit of a repetitive way
```
<div id="app>
    <input type="checkbox" id="john" value="John" v-model="checkedNames">
    <label for="john"> John</label>

     <input type="checkbox" id="paul" value="paul" v-model="checkedNames">
    <label for="paul"> Paul</label>
    <span>Checked names: {{ checkedNames }}</span>
</div> 
```

* Example using more dynamic & less repetitive version using `v-for` & `v-model` -> avoid hard coding here

```
<div id="app>
    <span v-for="option in options">
     <input type="checkbox"
     :id="option.value"
     :value="option.value"
     v-model="checkedNames">
        <label for="option.value">
        {{ option.value }}
        </label>
        </span>

        <br>
        <span> Checked names: {{ checkedNames }} </span>
</div> 

```

## Modifiers
* Special postfix denoted by a dot, indicate that a directive should be bound in some special way - more on modifiers [here](https://vuejs.org/v2/guide/syntax.html#Modifiers)
* Some examples:
    * `v-model.trim` -> string any leading / trailing whitespace from string
    * `v-model.number` -> changes strings to number inputs 
    * `v.model.lazy` -> won't populate the content automatically -> wait to bind until an event happens (listens to change events instead of input) - not storing key strokes, only really storing once a button us clicked


## Conditional rendering

## `v-if` vs `v-show`
* Conditional that displays information depending on meeting a requirement - can be anything: buttons, forms, divs, components



```
new Vue({
    el: '#app',
    data() {
        return {
            tacos: ''
        }
    }
})
```

`v-if` example
```
<div id="app">
    <h3> What is your favourite kind of taco?</h3>
    <textarea v-model="tacos"></textarea>

    <br>
    <button type="submit" v-if="tacos">Let us know!</button>
</div>
```

* In dev tools -> with nothing typed into the input box inspecting the DOM can see an empty comment `<!------>` - as soon as it's populated with some text the button appears
* `v-if` will unmount & mount element into the DOM



`v-show` example
```
<div id="app">
    <h3> What is your favourite kind of taco?</h3>
    <textarea v-model="tacos"></textarea>

    <br>
    <button type="submit" v-show="tacos">Let us know!</button>
</div>
```
* When no text is there the button disappears with a `style="display:none`
* `v-show` is just toggling visibility of an element rather than completely mounting / un-mounting -> could be more performant if users might be often clicking on this , rather than re-rendering every time
* However if using a component as a one off -> load time will be smaller using `v-if`


## `v-if` vs `v-else`
* Conditionally render one thing or another, also there's `v-else-if`
```
<div id="app">
    <h3> What is your favourite kind of taco?</h3>
    <textarea v-model="tacos"></textarea>

    <br>
    <div v-if="tacos">
        <p v-if="tacos === 'yes'" class="thumbs">👍</p>
        <p v-else>👎</p>
</div>
```
* 'yes' is a string

