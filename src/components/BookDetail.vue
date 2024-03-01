<script setup>
import { onMounted, ref } from "vue";

// Ocultar el detalle
const emits = defineEmits(["hideDetail"]);

const props = defineProps(["selectedBookId"]);

const book = ref();

async function getBook() {
  const request = await fetch(
    "https://www.dbooks.org/api/book/" + props.selectedBookId
  );
  const response = await request.json();
  book.value = response;
}

onMounted(getBook);
</script>

<template>
  <section>
    <button @click="emits('hideDetail')" type="button">Atrás</button>
    <h2>Detalle del Libro</h2>
    <div class="detail-container">
      <img :src="book?.image" alt="" />
      <div>
        <p>
          <span>Titulo: {{ book?.title }}</span
          >este es un titulo
        </p>
        <p>
          <span>Subtitulo: {{ book?.subtitle }} </span>
        </p>
        <p>
          <span>Autores: {{ book?.authors }}</span>
        </p>
        <p>
          <span>Páginas: {{ book?.pages }}</span>
        </p>
        <p>
          <span>Año de publicación: {{ book?.year }}</span>
        </p>
        <p>
          <span>Editorial: {{ book?.publisher }}</span>
        </p>
        <a :href="book?.download" type="button">Descargar</a>
        <button type="button">Crear Reseña</button>
      </div>
    </div>
    <div>
      <p><span>Descripción: </span> {{ book?.description }}</p>
    </div>
  </section>
</template>

<style scoped>
section {
  max-width: 600px;
}
h2 {
  text-align: center;
  font-weight: 600;
}
.detail-container {
  margin-top: 30px;
  display: flex;
}
img {
  width: 50%;
}
.detail-container > div {
  width: 50%;
}
span {
  font-weight: 600;
}
</style>
