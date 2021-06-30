<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ToDoList msg="TodoList avec  Vue.js App"/>
     
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'App',
  components: {
    ToDoList
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
  
  background-color:#F8F8FA;

}
</style>
