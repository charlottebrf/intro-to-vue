## Filters 

* Not good for filtering content, like computed values.
* Don't alter the data
* They aren't replacements for methods, computed values or watchers because they don't transform the data - just the output that the user sees.
* Filters are re-run on every single update, better to use computed values for lots of data so they can be cached

```
// global instance
vue.filter(filtername, function(value) {
    return // thing to transform
})

//locally, like methods or computed 

filters: {
    filterName(value) {
        return // thing to transform
    }
}
```

Use it like this:
 
 ```
 {{ data | filter }}

// example
  {{ text | capitalise }}
 ```

 * Purely presentational - good examples, formatting dates
 * Can chain filters , e.g. `{{ data | filterA | filterB }}`

 * Can pass arguments
 ` {{ data | filterA(arg1, arg2)`