<script setup lang="ts">
  import {reactive} from "vue";
  import axios from 'axios';
  import router from "@/router";
  import {RouterLink} from "vue-router";
  import UnAuth from "@/components/UnAuth.vue";

  const formInput = reactive({
    userId: '',
    password:'',
    username:'' ,
    email:'' ,
    biography:''
  })

  const postForm = function(){
    axios.post('http://localhost:8080/api/user',{
      userId: formInput.userId,
      password: formInput.password,
      username: formInput.username,
      email: formInput.email,
      biography: formInput.biography
    }).then((res)=>{
      console.log("success!");
      console.log(res.data);
      alert("Register Success!!");
      router.push('/login')
    }).catch((err)=>{
      console.log("error");
      console.log(err);
    })
  }
</script>

<template>
  <div>
    <UnAuth />
    <form action="/login" method="post" autocomplete="on">
      <div>
        <label for="userId">帳號：</label>
        <input id="userId" type="text" v-model="formInput.userId"/>
      </div>
      <div>
        <label for="password">密碼：</label>
        <input id="password" type="password" v-model="formInput.password"/>
      </div>
      <div>
        <label for="username">名稱：</label>
        <input id="username" type="text" v-model="formInput.username"/>
      </div>
      <div>
        <label for="email">信箱：</label>
        <input id="email" type="text" v-model="formInput.email"/>
      </div>
      <div>
        <label for="biography">簡介：</label>
        <input id="biography" type="text" v-model="formInput.biography"/>
      </div>
      <div>
        <button @click.prevent="postForm">送出</button>
      </div>
    </form>
  </div>
</template>

<style scoped>
  div {
    width: 100%;
    font-size: 12px;
    text-align: center;
    margin-top: 1rem;
  }

  form {
    width: 100%;
    font-size: 12px;
    text-align: center;
    margin-top: 2rem;
  }
</style>