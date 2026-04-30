<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const txt = ["Beginner Frontend Dev", "Beginner Pentester", "Discord Bot Dev", "Artist"];

const display = ref("");
let tIndex = 0;
let cIndex = 0;
let isDel = false;
let to = null;

function type() {
  const curr = txt[tIndex];

  if (!isDel) {
    display.value = curr.slice(0, cIndex + 1);
    cIndex++;
    if (cIndex === curr.length) {
      isDel = true;
      to = setTimeout(type, 1500);
      return;
    }
  } else {
    display.value = curr.slice(0, cIndex - 1);
    cIndex--;
    if (cIndex === 0) {
      isDel = false;
      tIndex = (tIndex + 1) % txt.length;
    }
  }
  const s = isDel ? 50 : Math.random() * 100 + 60;
  to = setTimeout(type, s);
}

onMounted(() => type());
onUnmounted(() => clearTimeout(to));
</script>

<template>
  <section class="font-sans text-white py-20 mt-35">
    <div class="flex flex-col mx-auto max-w-6xl gap-6 px-6">
      <div class="flex flex-col sm:flex-row items-center gap-3">
        <img
          src="@/assets/profile/Profile.png"
          class="w-44 h-44 sm:w-52 sm:h-52 rounded-2xl object-cover pointer-events-none select-none"
        />
        <div class="flex flex-col justify-center mt-0 sm:mt-18 w-full">
          <h1 class="font-sans text-white/70 font-extralight text-3xl leading-tight">Hi, I'm</h1>
          <h1
            class="font-quicksand leading-none text-3xl sm:text-5xl font-normal mb-2 animate-glow tracking-tighter"
          >
            Aarchfel
          </h1>
          <p
            class="font-quicksand text-white/65 text-lg sm:text-xl min-h-7 sm:min-h-8 overflow-hidden whitespace-nowrap"
          >
            {{ display }}<span class="animate-blink">|</span>
          </p>
        </div>
      </div>
      <p class="text-white/65 text-lg">
        Greetings! I'm Fel or you can call me Aarch or Archie! I'm a 14 years old programmer and
        beginner pentester and an Artist! I love to explore things!
      </p>
      <div class="flex flex-wrap gap-5 mt-12">
        <a href="#about" class="profile-primbtn">
          Learn More
          <img src="@/assets/profile/learn.svg" alt="Learn More" class="w-5 h-5 pl-1" />
        </a>
        <a href="#projects" class="profile-secbtn">View Projects</a>
        <a href="#contact" class="profile-secbtn">Contact</a>
      </div>
    </div>
  </section>
</template>
