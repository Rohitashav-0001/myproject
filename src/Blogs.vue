<template>
    <div id = "blogs">
        <h2>{{ blogTitle | Upper }}</h2>
        <input type = "text" v-model = "searchTerm"><br>
        <button @click = "changeTitle">Change Title</button>
        <!--cycling through posts-->
        <div  v-for="post in filteredPosts" :key = "post.id">
            <h3>{{ post.title }}</h3>
            <!--filters(snippet-filtername)-->
            <P> {{ post.body | snippet}} </P> 
        </div>
    </div>
</template>

<script>
import axios from 'axios'  //axios is defined in node modules

export default {
    name:'blogs',
    data(){
        return {
            blogTitle:  'Blogs',
            posts: [],
            searchTerm: ''
        }
    },
    methods:{
        changeTitle(){
            this.blogTitle = 'Amazing Blog Website'
        }
    },
    computed: {
        filteredPosts(){
            return this.posts.filter(post => {
                return post.title.match(this.searchTerm) 
                //match function takes the value of post tilte and matches it against the searchTerm
            })
        }
    },
    //creating local filter
    filters:{
        Upper(value){
            return value.toUpperCase();
        }
    },
    created(){      //lifecycle hooks,does not go inside the methods
        ///making requests with axios(an ajax library to grab data from api)
        axios.get('https://jsonplaceholder.typicode.com/posts/')
        .then(response => {
            console.log(response)
            this.posts = response.data
        })
    },
    /*beforeUpdate(){
        alert('beforeUpdate hook cycle')
    }*/

 }
</script>

<style>

</style>