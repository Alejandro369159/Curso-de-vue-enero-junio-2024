<script setup>
defineProps(["book"]);
</script>

<template>
  <div class="book-card">
    <img
      src="https://th.bing.com/th/id/OIP.0MCwGzmvISrGyIc2B2xKdgHaE8?rs=1&pid=ImgDetMain"
      alt=""
    />
    <div>
      <p>Titulo: {{ book.title }}</p>
      <p>Subtitulo: {{ book.subtitle }}</p>
      <p>Autores: {{ book.authors }}</p>
    </div>
  </div>
</template>

<style scoped></style>
