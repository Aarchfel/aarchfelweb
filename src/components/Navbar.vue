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
  <nav
    class="font-sans fixed flex items-center w-full z-10 h-20 box-border px-6 md:px-[15%] backdrop-blur-md border-b bg-neutral-900/70 border-b-white/5 transition-transform duration-300 ease-in-out bg-[linear-gradient(to_right,rgba(23,23,23,0.3)_75%,rgba(255,255,255,0.06))] overflow-hidden"
    :class="{ '-translate-y-full': hidden }"
  >
    <a
      href="#home"
      class="group text-2xl font-quicksand font-medium flex items-center gap-1.5 text-white/50 transition-colors duration-200 hover:text-white/90"
      ><img
        src="@/assets/paws.svg"
        class="w-5 h-5 opacity-50 transition-opacity duration-200 group-hover:opacity-90"
      />Aarchfel</a
    >
    <ul class="flex list-none gap-2 sm:gap-5 ml-auto">
      <li>
        <a href="#home" @click="onNavClick" class="nav-li">Home</a>
      </li>
      <li><a href="#about" @click="onNavClick" class="nav-li">About</a></li>
      <li><a href="#projects" @click="onNavClick" class="nav-li">Projects</a></li>
      <li><a href="#contact" @click="onNavClick" class="nav-li">Contact</a></li>
    </ul>

    <div class="absolute -right-10 top-10 -translate-y-1/2 opacity-10 pointer-events-none">
      <img src="@/assets/star.svg" class="w-42 h-42 animate-swing select-none" alt="" />
    </div>
  </nav>
</template>
