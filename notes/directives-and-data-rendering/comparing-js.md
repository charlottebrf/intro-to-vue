# Comparison
* vanilla.js -> map over a list of 
* Yields the list with Vue & HTML - much more declarative style, rather than needing to write each step in a recipe
* Clean
* Semantic
* Declarative

.js
```
new Vue({
    el: '#app',
    data: {
        items: [
            'things',
            'things2',
            'things3',
            'things4',
        ]
    }
})
```

.html
```
<div id="app">
 <ul>
  <li v-for="item in items">
    {{ item }}
  </li>
 </ul>
</div>    
```