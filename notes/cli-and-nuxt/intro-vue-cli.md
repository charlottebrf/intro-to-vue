# Intro Vue CLI & nuxt

* Real build process for Vue - much for useful

# Why use it?
* Build processes that allow us to use great features like ES6 or SCSS, easy to use other libs
* Going to build & concatenate single file templates => great workflow
* To not load all files at startup: lazyload, async 
* Sever-side rendering, code-splitting, performance metrics
* Build / prod versions


```
npm install -g vue-cli

vue init webpack-simple my-project
cd my-project
npm install
npm run dev
```

* Webpack: testing, es-lint config etc - probably better than webpack-simple in prod
* Immediately gives us a dev server 

## Single file templates

```
< template>
    <div>
     <!-- HTML with Vue here - markup - we have to return a single element-->
    </div>
< /template>

<script>
 export default {
     // Vue component logic here
 }
</script>

<style scoped>
/* Write your styles for the component here*/
</style>
```
* Base of .vue => everything in one place, in a single file

```
import New from './components/New.vue'

export default {
    components: {
        New
    }
}

<new></new>
```
* Parent component, bringing in child templates

* Same thing written slightly differently
```
import New from './components/New.vue'

export default {
    components: {
        appNew: New
    }
}

<app-new></app-new>
```

https://github.com/sdras/intro-to-vue/tree/main/setup1