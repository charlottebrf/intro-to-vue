# Handling events

```
Vue.component('child', {
    props: ['text],
    template: '#child',
    methods: {
        talkToMe() {
            this.text = 'forget introduction, I want a taco',
            this.$emit('changeText', this.text)
        }
    }
});

var vm = new Vue({
    el: '#app',
    data() {
        return {
            message: 'hello mr.magoo'
        }
    }
 })

<div id='app'>
<child :text='message' @changeText="message = $event"></child>
</div>

<script type='text/x-template' id='child'>
    <div>
    <p> {{ text }} </p>
    <button @click="talkToMe"> Let's talk</button>
    </div>
</script>
```
* Mutating a prop directly - won't tell the child that something has changed
* Props are always parent to child communication - always going down, but not back up
* changeText is what gets moved down

```
<my-component @myEvent="parentHandler"></my-component>

methods: {
    fireEvent() {
        this.$emit('myEvent', eventValue, eventValueTwo)
    }
}
```
* `$emit` => $ means it's a special thing from Vue

* Need to make the child report it's activity to the parent


## With a method

```
methods: {
    heightIncrease: function () {
        this.count += 1
        this.$emit('heightincrease')
    }
}
```

```
<script type="text/x-template" id="height-counetr">
    <button @click="heightIncrease">Increase height </button>
</script>
```

* Child
* events using on the child don't have to be the same as the parent
```
  <button @click="heightIncrease">Increase height </button>
```

* Parent 
* Implements the height counter
* Alerting that something is happening but it doesn't have to be the same
* Relationship between click height increase
```
  <div class='button-group'>
  <button @click='animatedBall' v-if='!running>Start</button>
  <button @click='cancelAnimate' v-else>Reset</button>
   <height-counter @heightincrease='incrementHeight' ></height-counter>
  </div>
```