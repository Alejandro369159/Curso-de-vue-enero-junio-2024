<script setup>
import { ref } from "vue";
import LoginPage from "./pages/LoginPage.vue";
import NavBar from "./components/NavBar.vue";
import AboutUsPage from "./pages/AboutUsPage.vue";
import ExplorePage from "./pages/ExplorePage.vue";

const isLoginShown = ref(true);

// Navbar
// pageShown ("about-us" | "explore" | "reviews")
const pageShown = ref("about-us");

function changePage(page) {
  pageShown.value = page;
}
</script>

<template>
  <!-- Login -->
  <LoginPage @hide-login="isLoginShown = false" v-if="isLoginShown === true" />

  <!-- Contenido de la app -->
  <div v-else>
    <!-- Navbar -->
    <NavBar @change-page="changePage" @hide-login="isLoginShown = true" />
    <!-- Páginas -->

    <!-- Acerca de nosotros -->
    <AboutUsPage v-if="pageShown === 'about-us'" />

    <ExplorePage v-if="pageShown === 'explore'" />

    <section v-if="pageShown === 'reviews'">
      <h2>Reseñas</h2>
    </section>
  </div>
</template>

<style scoped></style>
