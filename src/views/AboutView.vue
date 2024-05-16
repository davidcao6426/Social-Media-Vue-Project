<script setup lang="ts">
import axios from 'axios'
import{reactive, onMounted} from 'vue';

const data = reactive({
  newsdata:'',
})

axios.defaults.baseURL = 'http://localhost:8080'
axios.get('/api/user/user',{
  params: {
    id: "176"
  }
})
    .then(function (response) {
      // handle success
      console.log("success");
      console.log(response.data);
      data.newsdata = response.data
      console.log(response.data.userId);
      console.log(response.data.email);
    })
    .catch(function (error) {
      // handle error
      console.log("error");
      console.log(error);
    })
    .finally(function () {
      // always executed
    });

</script>
<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h1>{{ data.newsdata }}</h1>
    <h1>{{ data.newsdata.userId }}</h1>
    <h1>{{ data.newsdata.email }}</h1>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
