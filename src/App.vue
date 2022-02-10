<script setup>
import Container from "./components/Container.vue";
</script>

<template>
  <Container class="container" />
</template>

<style>
@import url("../node_modules/normalize.css/normalize.css");
@import url("./assets/colors.css");
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@200;400;700&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  color: var(--color-primary-text);
  background: var(--color-background);

  width: 100vw;
  height: 100vh;

  display: flex;
  justify-content: center;
}

#app {
  font-family: "Inter", sans-serif;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  margin: 20px;

  max-width: 1440px;

  width: 100%;
}

.text {
  color: var(--color-text);
}
</style>
