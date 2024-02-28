<script setup>
import { ref } from "vue";
import LoginPage from "./pages/LoginPage.vue";
import NavBar from "./components/NavBar.vue";

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
    <section class="about-us-container" v-if="pageShown === 'about-us'">
      <img src="@/assets/images/books.jpg" alt="" />
      <h2>Acerca de nosotros</h2>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus,
        ea accusamus consequuntur quo fuga deleniti nostrum. Consequuntur qui
        optio, sed voluptas aut fugit quae, in voluptatibus inventore iusto
        maiores porro vel voluptatem rerum? Ullam, accusantium nobis!
        Cupiditate, perferendis aperiam. Iusto sequi magnam perferendis nostrum
        optio iure. Maiores, numquam qui ipsum esse voluptate vero maxime ad
        illum unde sed veritatis tenetur sint aspernatur, omnis tempora
        consectetur expedita nisi eaque dolorem temporibus aut harum. Corrupti
        commodi architecto sint consequatur quod ea aut deserunt quasi veniam
        dolores laborum atque at dolor excepturi labore natus est dolorem
        provident accusantium, dicta obcaecati minima nobis similique. Adipisci
        asperiores ipsum, reprehenderit numquam deserunt et. Accusantium ad
        nobis aperiam officiis aliquid provident, iure quia reiciendis possimus
        maxime incidunt illo, inventore expedita velit libero quis! Obcaecati
        consectetur illo quo iusto exercitationem asperiores, dolorum
        distinctio, blanditiis consequatur voluptates itaque nisi quaerat
        corrupti dolorem! Quisquam deleniti molestiae voluptatem, vitae
        similique numquam!
      </p>
    </section>

    <section v-if="pageShown === 'explore'">
      <h2>Explorar</h2>
    </section>

    <section v-if="pageShown === 'reviews'">
      <h2>Reseñas</h2>
    </section>
  </div>
</template>

<style scoped>
/* Acerca de nosotros */
.about-us-container {
  margin: auto;
  max-width: 700px;
}

.about-us-container > h2 {
  text-align: center;
  font-weight: 600;
}

.about-us-container > img {
  width: 100%;
}
</style>
