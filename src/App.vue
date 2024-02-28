<script setup>
import { ref } from "vue";
const email = ref();
const password = ref();

const isLoginShown = ref(true);

function login() {
  // Toda la lógica de autenticar al usuario
  if (email.value === "alejandro" && password.value === "abc") {
    // Ingresa a la app
    isLoginShown.value = false;
  } else {
    // Denegamos el acceso
    alert("Las credenciales son incorrectas");
  }
}

// Navbar
// pageShown ("about-us" | "explore" | "reviews")
const pageShown = ref("about-us");
</script>

<template>
  <!-- Login -->
  <div v-if="isLoginShown === true" class="login-container">
    <h1>Login</h1>
    <form @submit.prevent="login">
      <div>
        <label for="email">Email:</label>
        <input v-model="email" type="text" name="email" />
      </div>
      <div>
        <label for="password">Contraseña:</label>
        <input v-model="password" type="text" name="password" />
      </div>
      <button type="submit">Ingresar</button>
    </form>
  </div>

  <!-- Contenido de la app -->
  <div v-else>
    <!-- Página de acerca de nosotros -->
    <!-- Página de reseñas -->
    <!-- Página de explorar -->
    <nav>
      <h2>MyBooksApp</h2>
      <div>
        <span @click="pageShown = 'about-us'">Acerca de nosotros</span>
        <span @click="pageShown = 'explore'">Explorar</span>
        <span @click="pageShown = 'reviews'">Reseñas</span>
        <span @click="isLoginShown = true">Cerrar sesión</span>
      </div>
    </nav>
    <!-- Páginas -->
    <section v-if="pageShown === 'about-us'">
      <h2>Acerca de nosotros</h2>
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
/* Login */
.login-container {
  width: 400px;
  margin: 100px auto;
  background-color: rgb(237, 245, 252);
  padding-block: 30px;
  border-radius: 30px;
}

.login-container > h1 {
  text-align: center;
  font-weight: 600;
}

.login-container > form {
  display: block;
  padding: 20px 40px;
}

form > div > label {
  display: block;
  font-weight: 500;
}

form > div > input {
  margin-top: 5px;
  margin-bottom: 10px;
  display: block;
  width: 100%;
  border: 0;
  padding: 12px 10px;
  border-radius: 6px;
}

form > button {
  margin: 40px auto auto auto;
  display: block;
  cursor: pointer;
  border: 0;
  padding: 8px 50px;
  background-color: rgb(153, 179, 243);
  color: white;
  font-weight: 600;
  font-size: 1rem;
  border-radius: 8px;
}

/* Navbar */
nav {
  display: flex;
  padding: 10px 20px;
  align-items: center;
  justify-content: space-between;
  background-color: white;
  width: 100%;
  border-bottom: 1px solid rgb(206, 206, 206);
  box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
}

nav > h2 {
  font-weight: 600;
}

nav > div > span {
  cursor: pointer;
  margin-right: 40px;
}
</style>
