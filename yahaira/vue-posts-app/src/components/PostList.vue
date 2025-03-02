<template>
    <div class="post-list">
    <h2>Listado de Posts</h2>  
    <ul>
      <li v-for="post in posts" :key="post.id">
        <div class="post-card">
        <h3>{{ post.title }}</h3>
        <p>{{ post.body }}</p>
        <button @click="verDetalle(post.id)">Ver más</button>
      </div>
      </li>
    </ul>
  </div>
</template>

<style scoped>

.post-list {
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  width: 80%;
  margin: auto;
  text-align: center;
  background-image: url('/fondo.png');
}

ul {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px; 
}

li {
  width: 100%;
  display: flex;
  justify-content: center;
}

.post-card {
  max-width: 700px;
  background: #d5f1f2;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
  text-align: center;
  width: 100%;
}

h3 {
  margin-bottom: 10px;
}

</style>

<script>
import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";

export default {
  setup() {
    const posts = ref([]);
    const router = useRouter();

    onMounted(async () => {
      const response = await fetch("https://jsonplaceholder.typicode.com/posts");
      posts.value = await response.json();
    });

    const verDetalle = (id) => {
      router.push(`/post/${id}`);
    };

    return { posts, verDetalle };
  },
};
</script>
