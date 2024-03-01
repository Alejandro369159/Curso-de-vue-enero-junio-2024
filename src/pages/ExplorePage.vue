<script setup>
import BookCard from "@/components/BookCard.vue";
import { ref, onMounted } from "vue";

const books = ref([]);

async function getBooks() {
  // Lógica de traerme los libros de la API
  const request = await fetch("https://www.dbooks.org/api/recent");
  // Esperar hasta la acción de arriba se complete
  const response = await request.json();
  books.value = response.books;
}

onMounted(getBooks);
</script>

<template>
  <section>
    <h2>Explorar Libros</h2>
    <div>
      <!-- Una sola instancia de un libro -->
      <BookCard v-for="_book in books" :book="_book" />
    </div>
  </section>
</template>

<style scoped>
section {
  max-width: 800px;
  margin: auto;
  margin-top: 30px;
}

h2 {
  text-align: center;
}
</style>
