<template>
<form @submit.prevent="submit"> <!-- prevent = 이벤트를 블로킹 -->
  <div>
    <label for="username">id:</label>
    <input id="username" type="text"
           v-model="username" />
  </div>
  <div>
    <label for="password">pw:</label>
    <input id="password" type="password"
           v-model="password" />
  </div>
  <button>login</button>
</form>
</template>

<script>
import axios from 'axios';

export default {
  data   : function(){
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    submit: function(){
      let url = 'https://jsonplaceholder.typicode.com/users';
      let data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
           .then(function(res){
             console.log(res);
           })
           .catch(function(err){
             console.log(err);
           });
    }
  }
}
</script>

<style>

</style>
