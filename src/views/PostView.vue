<script setup lang="ts">
  import {reactive} from "vue";
  import axios from 'axios'

  const url = new URL(window.location.href);
  const params = new URLSearchParams(url.search);
  const postId = params.get("postId");

  const data = reactive({
    // col_data : [
    //   "作者", "文章"
    // ],
    api_data: { postId:'', userId:'', title:'', content: '', createAt: '', comments: [
        { commentId:'', userId:'', postId:'', content:'', createAt: ''}
      ]}
  })

  axios.get('http://localhost:8080/api/post/'+postId)
    .then((res)=>{
      console.log("success!");
      console.log(res.data);
      if(res.data){
        console.log("success");
        console.log(res.data);
        data.api_data = res.data;
      }
    }).catch((err)=>{
      console.log("error");
      console.log(err);
    })

  const comment = function(){
    
  }
</script>

<template>
  <div class="content_container">
    <div class="title">
      <h1>{{ data.api_data.title }}</h1>
    </div>
    <div class="user">
      <h2>發文者：{{ data.api_data.userId }}</h2>
      <div>發文時間： {{ data.api_data.createAt }} </div>
    </div>
    <div class="content">
      <div>
        <pre>{{ data.api_data.content }}</pre>
      </div>
    </div>
    <div class="actionBtn">
      <button @click.prevent="comment">留言</button>
    </div>
    <div class="commentList">
      <div v-for="(item, index) in data.api_data.comments" :key="item.commentId" class="form-item">
        <div>
          <a>{{ item.userId }} </a>
          <pre>{{ item.content }} </pre>
        </div>
        <div>
          {{index+1}}樓
          <span class="time">{{ item.createAt }} </span>
        </div>

      </div>
    </div>
  </div>

<!--  <table class="commentList">-->
<!--    <tr>-->
<!--      <td v-for="item in data.col_data" class="form-head">{{ item }} </td>-->
<!--    </tr>-->
<!--    <tr v-for="item in data.api_data" :key="item.userId" class="form-item">-->
<!--      <td>{{ item.userId }} </td>-->
<!--      <td>-->
<!--        <a :href=" '/post?postId='+ item.postId">-->
<!--          {{ item.title }}-->
<!--        </a>-->
<!--      </td>-->
<!--    </tr>-->
<!--  </table>-->
</template>

<style scoped>
  div {
    margin: 1rem;
  }

  .content_container {
    border-style:solid;
  }
  .title {
    border-style:solid;
  }
  .title h1 {
    margin-top: 1rem;
    margin-bottom: 1rem;
    margin-left: 1rem;
  }

  .user {
    border-style:solid;
  }
  .user h2 {
    margin-top: 1rem;
    margin-bottom: 1rem;
    margin-left: 1rem;
  }

  .content {
    border-style:solid;
  }
  .content div {
    font-size: 14px;
    margin-top: 1rem;
    margin-bottom: 1rem;
    margin-left: 1rem;
  }

  .actionBtn {
    text-align: center;
  }

  .commentList {
    border-style:solid;
  }

  .time {
    text-align: right;
  }

  .form-item {
    border-style:solid;
  }

</style>