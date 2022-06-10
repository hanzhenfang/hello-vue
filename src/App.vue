
<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld11 /> -->
  <TodolistDemo />
</template>

<script>
// import HelloWorld11 from "./components/HelloWorld.vue";
import TodolistDemo from "./components/todoList.vue";

export default {
  name: "App",
  components: {
    // HelloWorld11,
    TodolistDemo,
  },
};
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
