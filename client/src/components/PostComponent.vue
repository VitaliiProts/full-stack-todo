<template class="wrapper">
  <section class="container">
    <h1>todo</h1>
    <input type="text" placeholder="Create post" v-model="text" @keyup.enter="createPost" class="new-todo">    
    <hr>
    <p v-if="error">{{ error }}</p>
    <div v-for="(post, index) in posts"
        :item="post"
        :index="index"
        :key="post._id"
    >
    <div>
      <span>{{ `${post.createdAt.getDate()}/${post.createdAt.getMonth()}/${post.createdAt.getFullYear()} - ` }}</span>
      <span>{{ post.text }}</span>
      <button @click="deletePost(post._id)">x</button>
    </div>
    </div>
  </section>
</template>

<script src="./index.js"></script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style src="./index.scss" scoped lang="scss"></style>
