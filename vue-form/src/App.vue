<template>
  <form v-on:submit.prevent="submetForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from 'axios'

export default {
  // 컴포넌트간 데이터가 겹치지 않게 function을 연결해서 새 객체를 return 하는 구문
  data: function() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    submetForm: function() {

      console.log(this.username, this.password)
      var url = 'https://jsonplaceholder.typicode.com/users'
      var data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
      .then(function(response) {
        console.log(response)
      })
      .catch(function(error) {
        console.log(error)
      })
    }
  }
}
</script>

<style>

</style>