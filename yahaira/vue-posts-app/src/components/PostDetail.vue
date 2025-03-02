<template>
    <div>
      <h1>Detalle del Post</h1>
      <p>Aquí se mostrará la información del post seleccionado.</p>
      <div v-if="post">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
    <button @click="$router.push('/')">Volver</button>
    </div>
  </template>
  
  <script>
  export default {
    name: "PostDetail",
    data() {
    return {
      post: null,
    };
  },
  methods: {
    async obtenerDetallePost() {
      try {
        const id = this.$route.params.id;
        const respuesta = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`);
        this.post = await respuesta.json();
      } catch (error) {
        console.error("Error al obtener el detalle del post:", error);
      }
    },
  },
  mounted() {
    this.obtenerDetallePost();
  },
  };
  </script>
  