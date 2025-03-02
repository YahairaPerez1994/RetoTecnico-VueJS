<template>
    <div>
      <h1>Detalle del Post</h1>
      <p>Aquí se mostrará la información del post seleccionado.</p>
      <div v-if="post">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
      <p><strong>Visitas:</strong> {{ numeroVisitas }}</p>
    </div>

    <h3>Comentarios</h3>
    <ul v-if="comments.length > 0">
      <li v-for="comment in comments" :key="comment.id">
        <strong>{{ comment.email }}</strong>: {{ comment.body }}
      </li>
    </ul>
    <p v-else>No hay comentarios disponibles.</p>

    <button @click="$router.push('/')">Volver</button>
  </div>
  </template>
  
  <script>
  export default {
    name: "PostDetail",
    data() {
    return {
      post: null,
      comments: [],
      numeroVisitas: 0,
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
    async obtenerComentarios() {
      try {
        const id = this.$route.params.id;
        const respuesta = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}/comments`);
        this.comments = await respuesta.json();
      } catch (error) {
        console.error("❌ Error al obtener los comentarios:", error);
      }
    },
  },
  mounted() {
    this.obtenerDetallePost();
    this.obtenerComentarios();
    this.numeroVisitas++;
  },
  };
  </script>
  