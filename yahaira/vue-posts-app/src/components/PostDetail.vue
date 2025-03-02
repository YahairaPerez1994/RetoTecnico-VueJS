<template>
    <div class="modal-overlay" @click.self="cerrarModal">
      <div class="modal-content">
      <div v-if="post">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
      <p><strong>Vistas:</strong> {{ numeroVisitas }}</p>
    </div>

    <h3>Comentarios</h3>
    <ul v-if="comments.length > 0">
      <li v-for="comment in comments" :key="comment.id">
        <strong>{{ comment.email }}</strong>: {{ comment.body }}
      </li>
    </ul>

    <button @click="cerrarModal">Cerrar</button>
  </div>
</div>
</template>

<style scoped>

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  max-width: 750px;
  width: 90%;
  text-align: center;
  background-image: url('/fondo.png');
}

</style>

  <script>
  export default {
    name: "PostDetail",
    props: ["postId"],
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
        const respuesta = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.postId}`);
        this.post = await respuesta.json();
      } catch (error) {
        console.error("Error al obtener el detalle del post:", error);
      }
    },
    async obtenerComentarios() {
      try {
        const respuesta = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.postId}/comments`);
        this.comments = await respuesta.json();
      } catch (error) {
        console.error(" Error al obtener los comentarios:", error);
      }
    },
      cerrarModal() {
        this.$emit("cerrar"); 
    },
  },
  mounted() {
    if (!this.postId) return;

    // Obtener visitas previas desde localStorage
    this.numeroVisitas = parseInt(localStorage.getItem(`visitas_post_${this.postId}`)) || 0;
    this.numeroVisitas++;

    // Guardar nuevamente en localStorage
    localStorage.setItem(`visitas_post_${this.postId}`, this.numeroVisitas);

    this.obtenerDetallePost();
    this.obtenerComentarios();
  },
  };
  </script>
  