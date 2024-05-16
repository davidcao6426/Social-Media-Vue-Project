<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import axios from 'axios'
axios.defaults.baseURL = 'http://localhost:8080'

function addUser(){
  axios.post('/api/user/user',{
    userId: "5564645645",
    username: "First",
    email: "davidcao6426@gmail.com",
    password: "hl654d93",
    coverImage: "123",
    biography: "text_text"
  })
      .then(function (response) {
        // handle success
        console.log("success");
        console.log(response);
      })
      .catch(function (error) {
        // handle error
        console.log("error");
        console.log(error);
      })
      .finally(function () {
        // always executed
      });
}


</script>

<template>
  <main>
    <TheWelcome />
  </main>
</template>
