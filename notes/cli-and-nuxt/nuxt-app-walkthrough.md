# Nuxt app walkthrough

```
npm install -g vue-cli

vue init nuxt/starter my-project
cd my-project
npm install
npm run dev
```

https://github.com/sdras/intro-to-vue/tree/main/setup2

* Get a different local host server
* Have some routing 
* No html.index file => `nuxt.config.js` - use this to configure this
* Any Vue file is a separate page that can be routed to automatically 
* `nuxt-link` => a routing link to get from one page to another `nuxt-link exact to=my-page"`
* Whatever is in pages is going to be inserted into `default.vue`
* Can also use this inside the pages, not only as external pages
* To use different style sheets, in css head tag can specify `{ ..., loading: false, css: [`assets/stuff`, `assets/stuff2`]}`