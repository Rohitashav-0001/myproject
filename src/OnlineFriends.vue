<template>
    <div id = "online-friends">
         <h2>Online Friends</h2>
         <div v-for= "(friend, index) in friends" :key= "index">
            <span v-if= "friend.online"> {{friend.name}} </span>
        </div>
    </div>
   
</template>

<script>
export default {
    name:'OnlineFriends',
    props: ['friends'], //receiving props from root file
    data(){
        return{
            
        }

    }
}
</script>

<style>
    h2{
    font-style:oblique;
    }
</style>