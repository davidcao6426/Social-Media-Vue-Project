<script setup lang="ts">
  import {reactive} from "vue";
  import axios from 'axios'
  import router from "@/router";
  import {RouterLink} from "vue-router";
  import UnAuth from "@/components/UnAuth.vue";
  import TheWelcome from "@/components/TheWelcome.vue";

  const formItems = reactive([
    { id: 'userId', label:'帳號(手機號碼)', type:'text', value:'' },
    { id: 'password', label:'密碼', type: 'password', value:'' },
    { id: 'username', label:'使用者名稱', type:'text', value:'' },
    { id: 'email', label:'信箱', type: 'email', value:'' },
    { id: 'biography', label:'簡介', type: 'text', value:''},
  ])

  const formInput = reactive({
    userId: '',
    password:'',
    username:'' ,
    email:'' ,
    biography:''
  })



  const postForm = function(){
    axios.post('http://localhost:8080/api/login',{
      userId: formInput.userId,
      password: formInput.password
    }).then((res)=>{
      console.log("success!");
      console.log(res.data);
      if(res.data){
        sessionStorage.setItem("userId", formInput.userId)
        router.push('/posts');
      }else{
        alert("帳號密碼錯誤!");
        router.push('/login');
      }

    }).catch((err)=>{
      console.log("error");
      console.log(err);
      alert("帳號密碼錯誤!");
      router.push('/login');
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
        <button @click.prevent="postForm">送出</button>
      </div>
    </form>
  </div>



<!--    <div v-for="item in formItems" :key="item.id" class="form-item">-->
<!--      <label :for="item.id">{{ item.label }}: </label>-->
<!--      <input-->
<!--          :type="item.type"-->
<!--          :id="item.id"-->
<!--          :name="item.id"-->
<!--          v-model="item.value"-->
<!--      />-->


<!--      />-->
<!--    </div>-->
<!--  div {-->
<!--  width: 100%;-->
<!--  font-size: 12px;-->
<!--  text-align: center;-->
<!--  margin-top: 2rem;-->
<!--  }-->
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