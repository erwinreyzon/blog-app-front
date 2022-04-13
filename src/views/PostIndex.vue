<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Blog Posts",
      posts: [],
    };
  },
  created: function () {
    axios.get("/posts.json").then((response) => {
      this.posts = response.data;
      console.log("Post Index", this.posts);
    });
  },
};
</script>

<template>
  <h1>{{ message }}</h1>

  <div v-for="post in posts" :key="post.id">
    <p>{{ post.title }}</p>
  </div>
</template>
