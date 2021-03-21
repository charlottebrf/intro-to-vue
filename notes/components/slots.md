# Slots

Great way to replace content without having to pass things down, like with props


```
<script type="text/x-template" id="childarea">
<div class="child">
    <slot></slot>
    <p>It's a variable slot machine</p>
</div>
</script>
``` 

```
<app-post>
    <h1 slot="header">This is the main title</h1>
    <p> I will go in unnamed slot</p>
</app-post>
```
* Inside the app - can use slot to populate content
* Didn't need to pass stuff down
* Could have a default slot
* Can have more than one , name them well
* Can dynamically change content / styling