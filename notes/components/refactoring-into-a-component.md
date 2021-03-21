# Refactoring into a component

* Have Vue instance & create components off it

* Small example using a template string
```
Vue.component('individual-comment', {
    template: 
    `<li> {{ commentPost }}</li>`,
    props: ['commentpost]
});
```
1. The template here is just a string but with the template interpolated in

```
<ul>
<li>
    is="invidual=comment"
    v-for="comment in comments"
    v-bind:commentpost="comment"
</li>
</ul>
```

2. Example of taking this a step further
```
Vue.component('individual-comment', {
    template: `#comment-templates`,
    props: ['commentpost]
});
```

* If you don't have a build process, you can use Vue with a script
* The comment-templates id is being pointed to in the html
```
<script type="text/x-template" id="comment-template">
<li>
   <img class="post-img" :src="commentpost.authoring"/>
    <email> {{ commentpost.author }} </email>
    <p class="post-comment"> "{{ commentpost.text }}"</p>
</li>
</script>
```
* Taking the inner text & replacing that
* Pass in all the information via a component in a much more straight forward way

## Another option: local component
* if it's all in one file

```
const IndividualComment = {
    template: `#comment-template`,
    props: ['commentpost']
}

new Vue({
    components: [
        `invidual-comment`: InvidualComment
    ]
})

```