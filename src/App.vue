<template>
  <div id="app">
      <h1>{{ title }}</h1>
      <Navbar />
      <AllFriends :friends = "friends" @delete = "deleteFriend" /> <!--passing props named friends from parent file-->
      <OnlineFriends :friends = "friends" />   <!--delete is received from child and is implemented in parent--> 
      <Blogs />  
  </div>
</template>

<script>
  import Navbar from './Navbar'
  import AllFriends from './AllFriends'
  import OnlineFriends from './OnlineFriends'
  import Blogs from './Blogs'
    
    export default {
    name: 'app',
    components:{
      Navbar,
      AllFriends, 
      OnlineFriends,
      Blogs
    },
    data () {
     return {
       title: 'My first Vue-application :)',
       friends: [
                { name : 'Sheldon Cooper', online:true},
                {name :'Howard Wolowitz', online:false},
                {name:'Leonard Hofstader', online:true},
                {name:'Rajesh Koothrapali', online:false}
            ]
      }
   },
   methods: {
     deleteFriend(pay){
          console.log(pay)
          this.friends = this.friends.filter(friend => {
            return friend.name !== pay.name
          })
      }
    } 
  } 
</script>

<style scoped>

  h1{
    text-align: center;
    font-style: oblique;
  }

</style>
