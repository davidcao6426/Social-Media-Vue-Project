<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <!-- <header> -->
<!--    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />-->

      <!-- <div> -->
<!--        <HelloWorld msg="You did it!" />-->
<!--        <div class="title">-->
<!--          Social Media Project-->
<!--        </div>-->

<!--        <nav>-->
<!--  &lt;!&ndash;        <RouterLink to="/">Home</RouterLink>&ndash;&gt;-->
<!--  &lt;!&ndash;        <RouterLink to="/about">About</RouterLink>&ndash;&gt;-->
<!--          <RouterLink to="/login">Login</RouterLink>-->
<!--          <RouterLink to="/register">Register</RouterLink>-->
<!--        </nav>-->
      <!-- </div> -->
  <!-- </header> -->
  <div class="container">
    <RouterView />
  </div>

</template>

<!--<style scoped>-->
<!--.container {-->
<!--  text-align: center;-->
<!--}-->
<!--.text {-->
<!--  position: relative;-->
<!--  top: 50%;-->
<!--  transform: translate(0, -50%);-->
<!--}-->

<!--</style>-->

<!--<style scoped>-->
<!--header {-->
<!--  line-height: 1.5;-->
<!--  max-height: 100vh;-->
<!--  padding-top: 25px;-->
<!--}-->

<!--.logo {-->
<!--  display: block;-->
<!--  margin: 0 auto 2rem;-->
<!--}-->

<!--nav {-->
<!--  width: 100%;-->
<!--  font-size: 12px;-->
<!--  text-align: center;-->
<!--  margin-top: 2rem;-->
<!--}-->

<!--nav a.router-link-exact-active {-->
<!--  color: var(&#45;&#45;color-text);-->
<!--}-->

<!--nav a.router-link-exact-active:hover {-->
<!--  background-color: transparent;-->
<!--}-->

<!--nav a {-->
<!--  display: inline-block;-->
<!--  padding: 0 1rem;-->
<!--  border-left: 1px solid var(&#45;&#45;color-border);-->
<!--}-->

<!--nav a:first-of-type {-->
<!--  border: 0;-->
<!--}-->

<!--.title {-->
<!--  display: flex;-->
<!--  place-items: center;-->
<!--  padding-right: calc(var(&#45;&#45;section-gap) / 2);-->
<!--}-->

<!--@media (min-width: 1024px) {-->
<!--  header {-->
<!--    display: flex;-->
<!--    place-items: center;-->
<!--    padding-right: calc(var(&#45;&#45;section-gap) / 2);-->
<!--  }-->

<!--  .logo {-->
<!--    margin: 0 2rem 0 0;-->
<!--  }-->

<!--  header .wrapper {-->
<!--    display: flex;-->
<!--    place-items: flex-start;-->
<!--    flex-wrap: wrap;-->
<!--  }-->

<!--  nav {-->
<!--    text-align: left;-->
<!--    margin-left: -1rem;-->
<!--    font-size: 1rem;-->

<!--    padding: 1rem 0;-->
<!--    margin-top: 1rem;-->
<!--  }-->
<!--}-->
<!--</style>-->
