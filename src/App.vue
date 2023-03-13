<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloTodo msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloTodo from './components/HelloTodo.vue'

export default {
  name: 'App',
  components: {
    HelloTodo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
