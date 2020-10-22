<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to My toDo List"/>
    <to-do-list name="Danh sách công việc" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import ToDoList from "./components/toDoList";

export default {
  name: 'App',
  components: {
    ToDoList,
    HelloWorld
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
