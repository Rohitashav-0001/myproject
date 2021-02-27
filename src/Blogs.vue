<template>
    <div id = "blogs">
        <h2>{{ blogTitle }}</h2>
        <button @click = "changeTitle">Change Title</button>
    </div>
</template>

<script>
export default {
    name:'blogs',
    data(){
        return {
            blogTitle: 'Blogs'
        }
    },
    methods:{
        changeTitle(){
            this.blogTitle = 'Amazing Blog Website'
        }
    },
    beforeCreate(){    //lifecycle hooks,does not go inside the methods
        alert('beforeCreate Hook')
    },
    created(){
        alert(' Created hook')
    },
    beforeUpdate(){
        alert('beforeUpdate hook cycle')
    }

 }
</script>

<style>

</style>