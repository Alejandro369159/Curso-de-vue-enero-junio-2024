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
    <button @click="emits('hideDetail')" type="button" class="go-back-btn">
      Atrás
    </button>
    <h2>Detalle del Libro</h2>
    <div class="detail-container">
      <img :src="book?.image" alt="" />
      <div>
        <p><span>Titulo: </span> {{ book?.title }}</p>
        <p><span>Subtitulo: </span> {{ book?.subtitle }}</p>
        <p><span>Autores: </span> {{ book?.authors }}</p>
        <p><span>Páginas: </span> {{ book?.pages }}</p>
        <p><span>Año de publicación: </span> {{ book?.year }}</p>
        <p><span>Editorial: </span> {{ book?.publisher }}</p>
        <a :href="book?.download" type="button"
          ><button type="button">Descargar</button></a
        >
        <button type="button">Crear Reseña</button>
      </div>
    </div>
    <div class="description-container">
      <span>Descripción: </span>
      <p>{{ book?.description }}</p>
    </div>
  </section>
</template>

<style scoped>
/* component container */
section {
  max-width: 700px !important;
}
/* go back button */
.go-back-btn {
  border: 0;
  width: 100px;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}
/* detail  */
h2 {
  text-align: center;
  font-weight: 600;
}
.detail-container {
  margin-top: 30px;
  display: flex;
}
img {
  width: 30%;
  padding: 5px;
  border-radius: 30px;
  object-fit: contain;
}
.detail-container > div {
  width: 70%;
  padding: 25px;
}
span {
  font-weight: 600;
}
a {
  text-decoration: none;
  color: white;
  font-weight: bold;
}
div > button {
  cursor: pointer;
  display: block;
  margin-bottom: 5px;
  border: 0;
  width: 250px;
  padding: 8px 20px;
  border-radius: 5px;
  font-weight: bold;
}

div > a > button {
  cursor: pointer;
  display: block;
  margin-bottom: 5px;
  border: 0;
  width: 250px;
  padding: 8px 20px;
  border-radius: 5px;
  font-weight: bold;
}

div > a:first-of-type > button {
  margin-top: 15px;
  background-color: rgb(69, 146, 247);
  color: white;
}

div > button:last-of-type {
  background-color: rgb(255, 179, 65);
  color: white;
}
/* Description */
.description-container {
  margin-top: 20px;
}
.description-container > span {
  padding-left: 10px;
}
.description-container > p {
  margin-top: 5px;
  background-color: rgb(242, 242, 242);
  padding: 10px;
  border-radius: 15px;
}
</style>
