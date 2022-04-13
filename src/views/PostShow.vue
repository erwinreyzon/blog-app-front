<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Blog Post",
      post: {},
    };
  },
  created: function () {
    axios.get("/posts/" + this.$route.params.id + ".json").then((response) => {
      console.log("Show Post", response.data);
      this.post = response.data;
    });
  },
};
</script>

<template>
  <h1>{{ message }}</h1>
  <h3>Title: {{ post.title }}</h3>
  <p>{{ post.body }}</p>
  <img :src="post.image" :alt="post.title" />
  <br />
  <a href="/posts">Back to Index</a>
  <br />
  <a href="/">Home</a>
</template>
