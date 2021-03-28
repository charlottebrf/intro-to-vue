# Vue CLI Walkthrough

* 
```
<link href="https://fonts.googleapis.com/css?family=Montserrat|PT+Serif" rel="stylesheet">
```

* Need to add in the manifest data
* No longer need to do `el: #app`
* Can add view css loader to import in more different types of css files
* app is like using the app file
* Noo need to bring the template over - because Vue knows about creating that relationship

`vimport`

`App.vue` => everything can go inside this main file
  
  * Once ready for deployment
  `npm run build`
  * `/dist` folder is used in prod 


  ## Overview
  * Start off with an App file in your `/src/` directory with `Hello.vue` file in `/components/` directory - see how imports & exports might work

* How Vue renders things into the page 

```

new Vue({
    el: `#app`,
    render: h =< h(App)>
})

```
* Arrow fn to create functional components => creates relationship with build process , passing app into the html