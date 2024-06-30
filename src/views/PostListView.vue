<script setup lang="ts">
  import {reactive} from "vue";
  import axios from 'axios'
  import router from "@/router";

  const data = reactive({
    col_data : [
        "作者", "文章"
    ],
    api_data: [
      { postId:'', userId:'', title:''},
    ]
  })

  const formInput = reactive({
    userId: sessionStorage.getItem("userId"),
    title:'',
    content:''
  })

  axios.defaults.baseURL = 'http://localhost:8080'
  axios.get('/api/posts')
      .then(function (response) {
        // handle success
        console.log("success");
        console.log(response.data);
        data.api_data = response.data;
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

  const postForm = function(){
    axios.post('http://localhost:8080/api/post',{
      userId: formInput.userId,
      title: formInput.title,
      content: formInput.content
    }).then((res)=>{
      console.log("success!");
      console.log(res.data);
      if(res.data){
        // router.push('/post');
        location.reload();
      }
    }).catch((err)=>{
      console.log("error");
      console.log(err);
    })
  }
</script>

<template>
  <div class="post">
<!--    <label>PostView</label>-->
    <form action="/post" method="post" autocomplete="on">
      <div>
        <label for="title">標題：</label>
        <input id="title" type="text" v-model="formInput.title" size="70" />
      </div>
      <div>
        <label for="content">內文：</label>
        <textarea id="content" type="text" v-model="formInput.content" rows="7" cols="67"/>
      </div>
      <button @click.prevent="postForm">發文</button>
    </form>
  </div>
  <table class="postList">
    <tr>
      <td v-for="item in data.col_data" class="form-head">{{ item }} </td>
    </tr>
    <tr v-for="item in data.api_data" :key="item.userId" class="form-item">
      <td>{{ item.userId }} </td>
      <td>
        <a :href=" '/post?postId='+ item.postId">
          {{ item.title }}
        </a>
      </td>
    </tr>
  </table>
</template>

<style scoped>
  div {
    font-size: 12px;
    margin-top: 1rem;
    margin-bottom: 1rem;
  }
  button {
    margin-bottom: 1rem;
  }
  label {
    text-align: top;
  }

  .post {
    border-style:ridge;
    width: 100%;
    text-align: center;
  }

  .postList {
    border-style:solid;
    width: 100%;
  }

  .form-head {
    border-style:solid;
  }

  .form-item {
    border-style:solid;
    color: gray;
    padding-left: 35%;
    text-align: left;
  }
</style>