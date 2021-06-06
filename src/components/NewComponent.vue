<template>
  <h3>Posts:</h3>
  <div v-if="!posts">loading...</div>
  <ul v-if="posts">
    <li v-for="post in posts.slice(5)" v-bind:key="post.title">
      {{ post.title }}
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "NewComponent",
  data(): { posts: Array<{ title: string }> | null } {
    return {
      posts: null,
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((stream) => stream.json())
      .then((data) => (this.posts = data));
  },
});
</script>
