# Keep alive

* Can maintain state as it switches between states

```
<keep-alive>
    <component :is="selected">
    ...
    </component>
</keep-alive>
```
* Retain state whilst going to next state - retain state of the component selected