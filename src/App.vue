<template>
  <div id="app">
    <input type="text" v-model="search" />
    <div v-for="post in filteredPosts" :key="post.id">
      <post :post="post"></post>
      <Treemap></Treemap>
    </div>
  </div>
</template>

<script>
import Post from "./components/Post";
import Treemap from "./components/Treemap";

export default {
  name: "App",
  components: {
    Post,
    Treemap,
  },
  data() {
    return {
      search: "",
      posts: [
        {
          id: 1,
          body: "Vue.js is cool",
        },
        {
          id: 2,
          body: "Javascript is cool",
        },
      ],
    };
  },
  computed: {
    filteredPosts() {
      return this.posts.filter((post) =>
        post.body.toLowerCase().includes(this.search.toLowerCase())
      );
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>