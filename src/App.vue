<template>
  <form v-on:submit.prevent="submitForm"> <!-- .prevent == .preventDefault();와 동일하게 작동 -->
    <div>
      <label for="username">id: </label>
      <input type="text" id="username" v-model="username"> <!-- username으로 입력받은 값을 username에 v-model을 이용해서 데이터 연결 -->
    </div>
    <div>
      <label for="password">pw: </label>
      <input type="password" id="password" v-model="password"> <!-- password으로 입력받은 값을 password에 v-model을 이용해서 데이터 연결 -->
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data: function(){
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    submitForm: function(){
      console.log(this.username, this.password);
      var url = 'https://jsonplaceholder.typicode.com/users';
      var data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
        .then(function(response){
          console.log(response);
        })
        .catch(function(error){
          console.log(error);
        });
    }
  }
}
</script>

<style>

</style>