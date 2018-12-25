<template>
  <section>
    <label for="create-post">Say something...</label>
    <input type="text" placeholder="Create post" v-model="text" @keyup.enter="createPost">    
    <button @click="createPost">Create post!</button>
    <hr>
    <p v-if="error">{{ error }}</p>
    <div v-for="(post, index) in posts"
        :item="post"
        :index="index"
        :key="post._id"
        @dblclick="deletePost(post._id)"
    >
    <span>{{ `${post.createdAt.getDate()}/${post.createdAt.getMonth()}/${post.createdAt.getFullYear()}` }}</span>
    <p>{{ post.text }}</p>
    </div>
  </section>
</template>

<script>
import PostService from "../PostService.js";

export default {
  name: "PostComponent",
  data() {
    return {
      posts: [],
      error: "",
      text: ""
    };
  },
  async created() {
    try {
      this.posts = await PostService.getPosts();
    } catch (err) {
      this.error = err.message;
    }
  },
  methods: {
    async createPost() {
      await PostService.insertPost(this.text);
      this.posts = await PostService.getPosts();
    },
    async deletePost(id) {
      await PostService.deletePost(id);
      this.posts = await PostService.getPosts();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
