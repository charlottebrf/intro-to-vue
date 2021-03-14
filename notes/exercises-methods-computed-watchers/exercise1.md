# Challenge 2: Updating a blog


* Need a list of blog posts 
* Make a new form that -> method where added blog posts go
* Filtering -> uses a computed property


* Baseline have blog posts
* https://codepen.io/sdras/pen/WOyjoj/


*Only submitting on the form submission rather than on a button
`<form  @submit.prevent="addPost">`
* Preventing from refreshing page with the `.prevent` modifier


* Filter by post or by i if it's there -> if no i then this still displays the default unfiltered view
    <div v-for="(post, i) in filterBy" :key="post.title" class="post">