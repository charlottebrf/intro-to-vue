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
* 'yes' is a string - it will show by

## `v-bind` or `:`
* V helpful class & style binding, creating dynamic props etc

```
<div id="app">
    <h3> What is your favourite kind of taco?</h3>
    <textarea v-model="tacos"></textarea>

    <br>
    <button> :class="[tacos ? activeClass : '']"> Let us know!
    </button>
</div>
```
* v-bind on the class -> ternary operator to choose something or not -> toggling styling using the `v-bind`
* In Directives can use ternaries but not more complex functions

## v-once & v-pre
```
<div id="app">
    <h3>What is your favorite kind of taco?</h3>
    <p><input v-model="tacos"/></p>
    <p v-once="tacos">{{ tacos }}</p>
    <span v-pre> This is good if I need to show the mustache view of {{ tacos }} </span>
    **/ this pre is pretty printing the data/**
    <pre> {{ $data }}</pre>
</div>

```


```
new Vue({
    el: '#app',
    data() {
        return {
            tacos: 'I like Al Pastor tacos'
        }
    }
})
```
* `v-once` will not update once it's rendered - only update on first time you enter it to the DOM
* `v-pre` will print out the inner text exactly how it is, including code (good for documentation)
* When you see this `$` you know it's something available & special from the Vue instance
* Could be useful for debugging -> can output what's going on with the data directly, similar to `JSON.stringify()`


## v-on or @
* Extremely useful so there's always a shortcut! 
* `v-on` is great for binding to events like click & mouseenter. You're able to pass in a parameter for the event like (e)
* Can also use ternaries directly
* attach to the dom element using `@`


```
<div id="app">
    <div class="quantity">
    <button class="inc" @click="counter"> 0 ? counter -=1 : 0">
    </button>
    <button class="inc" @click="counter += 1">
    </button>
    <button class="submit" @click="">
    Submit
    </button>
    </div>
</div>

```

```
new Vue({
    el: '#app',
    data() {
        return { counter: 0 }
    }
});
```
* Can connect this to methods as well

## Multiple bindings

```
<div v-on="
    click : onClick,
    keyup : onKeyup,
    keydown : onKeydown
">
</div>
```

## Modifiers
* `@mousemove.stop` -> comparable to `e.stopPropogation()`
* `@mousmove.prevent` -> like `e.preventDefault()`
* `@submit.prevent` -> will no longer reload the page on submission
* `@click.once` -> not to be confused with `v.once` -> this click event will be triggered once
* `@click.native` -> listen to native events in the DOM -> bit 
* keycodes are available - can easily figure your own

## v-html
* great for strings that have html elements that need to be rendered

```
<div id="app">
   <h3> What is your favourite kind of taco?</h3>
   <p v-html="tacos"></p>
</div>
```

```
    new Vue({
        el: '#app',
        data() {
            return {
                tacos: `I like <a href="some-website" target="_blank" Al Pastor<a/> tacos`
            }
        }
    })
```
* Want to output the url with the string attached
* Parse all of the tags
* Don't use this for user generated content - it's a security issue for XSS

## v-text
* Similar to using mustache templates

```
<div id="app">
   <h3> What is your favourite kind of taco?</h3>
   <p v-text="tacos"></p>
   <p> {{ tacos }} </p>
   <p><input v-model="tacos"/></p>
</div>
```
* Same as a mustache template basically
* Recommended to use mustache