<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const hidden = ref(false);
const lastY = ref(0);
const offset = 100;
let ignoreScroll = false;

function onScroll() {
  if (ignoreScroll) return;

  const curr = window.pageYOffset || document.documentElement.scrollTop;
  if (Math.abs(curr - lastY.value) < offset) return;
  hidden.value = curr > lastY.value;
  lastY.value = curr;
}

function onMouseMove(e) {
  if (e.clientY < 20) hidden.value = false;
}

function onNavClick() {
  hidden.value = false;
  ignoreScroll = true;
  setTimeout(() => {
    ignoreScroll = false;
    lastY.value = window.pageYOffset;
  }, 1100);
}

onMounted(() => {
  window.addEventListener("scroll", onScroll);
  window.addEventListener("mousemove", onMouseMove);
});

onUnmounted(() => {
  window.removeEventListener("scroll", onScroll);
  window.removeEventListener("mousemove", onMouseMove);
});
</script>

<template>
  <nav :class="{ hidden }">
    <a href="#home" class="logo"><img src="@/assets/home.svg" />Aarchfel</a>
    <ul>
      <li><a href="#home" @click="onNavClick">Home</a></li>
      <li><a href="#about" @click="onNavClick">About</a></li>
      <li><a href="#projects" @click="onNavClick">Projects</a></li>
      <li><a href="#contact" @click="onNavClick">Contact</a></li>
    </ul>
  </nav>
</template>

<style scoped>
body,
p,
a,
span {
  font-family: "Inter", sans-serif;
  font-weight: 340;
}

ul {
  display: flex;
  list-style: none;
  gap: 2rem;
  padding: 0;
  margin: 0;
  margin-left: auto;
}

li a {
  text-decoration: none;
  color: rgba(231, 227, 218, 0.778);
  font-size: 1em;
  cursor: pointer;
  transition: color 0.2s ease;
}

li a:hover {
  color: white;
}

nav {
  position: fixed;
  top: 0;
  display: flex;
  align-items: center;
  width: 100%;
  z-index: 100;
  height: 70px;
  box-sizing: border-box;
  padding: 0 2em;
  background: linear-gradient(to right, rgba(23, 23, 23, 0.6) 70%, rgba(255, 255, 255, 0.1));
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.07);
  transition: transform 0.2s ease;
}

nav.hidden {
  transform: translate3d(0, -100%, 0);
}

.logo {
  font-family: "Quicksand", sans-serif;
  font-size: 1.55em;
  font-weight: 550;
  text-decoration: none;
  color: rgba(245, 245, 220, 0.5);
  display: flex;
  align-items: center;
  gap: 6px;
  transition: color 0.2s ease;
}

.logo img {
  width: 1em;
  height: 1em;
  opacity: 0.5;
  transition: opacity 0.2s ease;
}

.logo:hover {
  color: beige;
}

.logo:hover img {
  opacity: 1;
}
</style>
