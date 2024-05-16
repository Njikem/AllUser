<template>
  <div id="app">
    <h2>This is all good</h2>
   <div v-for="(user, i) in users" :key="i">
     <h3>
        {{user.id}}
     </h3>
     <h3>
        {{user.email}}
        </h3>
     <h3>
        {{user.first_name}}
        </h3>
     <h3>
        {{user.last_name}}
        
        </h3>
    <h3>
        {{user.avatar}}
        </h3>

   </div>
    
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'AllUser',
  components: {
  },

  data: function(){
     return {
        users: []
     }
  },

  methods: {
    success: function(response){
        console.log(response);
        if(response.status ===200){
            this.users = response.data.data
            console.log(this.users);
        }
        
    },

    failure: function(error){
        console.log(error);
        console.log("error has occured")
    }

  },

 mounted: function(){
    axios.request({
        url: 'https://reqres.in/api/users',
    })
    .then(this.success)
       
    .catch(this.failure) 
   
 },

}

</script>

<style>

</style>
