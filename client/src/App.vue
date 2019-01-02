<template>
  <div id="app">
    <post-component msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import PostComponent from "./components/PostComponent.vue";

export default {
  name: "app",
  components: {
    PostComponent
  }
};
</script>

<style lang="scss">
  body {
  font-family: Palatino, serif;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #888;
  }
</style>
