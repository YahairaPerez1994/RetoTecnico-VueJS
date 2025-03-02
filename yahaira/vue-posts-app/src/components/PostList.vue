<template>
  <div>
    <h1>Listado de Posts</h1>
    <p>Aquí se mostraran los posts.</p>
    
    <ul>
      <li v-for="post in posts" :key="post.id">
        <h3>{{ post.title }}</h3>
        <p>{{ post.body }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";

export default {
  setup() {
    const posts = ref([]);

    onMounted(async () => {
      const response = await fetch("https://jsonplaceholder.typicode.com/posts");
      posts.value = await response.json();
    });

    return { posts };
  },
};
</script>
