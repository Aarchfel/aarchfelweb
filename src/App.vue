<script setup>
import NavBar from "./components/Navbar.vue";
</script>

<template>
  <NavBar />
  <RouterView />
</template>

<style>
html {
  scroll-behavior: smooth;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: rgb(23, 23, 23);
  overflow-x: hidden;
}
</style>
