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
  <section>
    <div class="hero">
      <div class="profile">
        <img src="@/assets/profile/Profile.png" class="pfp" />
        <div class="text">
          <h1>Hi, I'm</h1>
          <h1 class="name">Aarchfel</h1>
          <p class="desc">{{ display }}<span class="cursor">|</span></p>
        </div>
      </div>
      <p class="bio">
        Hello! I'm Fel or you can call me Aarch or Archie! I'm a 14 years old programmer and
        beginner pentester and an Artist! I love to explore things!
      </p>
      <div class="cta-buttons">
        <a href="#about" class="about">
          Learn More
          <img src="@/assets/profile/learn.svg" alt="Learn More" />
        </a>
        <a href="#projects" class="btn">View Projects</a>
        <a href="#contact" class="btn">Contact</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
h1,
h2,
h3 {
  font-family: "Quicksand", sans-serif;
}

h1 {
  font-weight: 300;
}

body,
p,
a,
span {
  font-family: "Inter", sans-serif;
  font-weight: 290;
}

section {
  min-height: calc(120vh - 270px);
  display: flex;
  align-items: center;
  padding-top: 70px;
}

.hero {
  width: 70%;
  margin-left: 15%;
  display: flex;
  flex-direction: column;
  gap: 1.7rem;
}

.profile {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.pfp {
  width: 190px;
  height: 190px;
  border-radius: 6%;
  object-fit: cover;
  inset: 0;
  transition:
    transform 0.25s ease,
    box-shadow 0.25s ease;
}

.pfp:hover {
  transform: translateY(-3%) scale(1.02);
  box-shadow: 0 5px 16px rgba(0, 0, 0, 0.34);
}

.text {
  color: white;
  margin: 0;
  margin-top: 5%;
}

.name {
  font-size: 3em;
  border-radius: 10px;
  display: inline-block;
  font-weight: 400;
  margin-bottom: 0;
  animation: glowPulse 5s infinite alternate;
}

.desc {
  font-size: 1.3em;
  margin: 0;
  color: rgba(245, 245, 245, 0.685);
}

.bio {
  font-size: 1.2em;
  color: rgba(245, 245, 245, 0.685);
  margin: 0;
}

.cta-buttons {
  display: flex;
  gap: 1.2em;
  margin: 0;
  margin-top: 3em;
  padding: 0;
}

.cta-buttons a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.4em 1em;
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.07);
  color: white;
  text-decoration: none;
  font-size: 1.2em;
  cursor: pointer;
  transition: all 0.2s ease;
}

.about {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(4px);
}

img {
  width: 1.2em;
  height: 1.2em;
  padding-left: 5px;
}

.about:hover {
  background: rgba(255, 255, 255, 0.36);
  box-shadow: 0 0 14px rgba(255, 255, 255, 0.34);
}

.btn {
  background: transparent;
}

.btn:hover {
  background: rgba(255, 255, 255, 0.1);
}

.cursor {
  animation: blink 1s step-start infinite;
  color: rgba(245, 245, 245, 0.685);
}

@keyframes glowPulse {
  0% {
    text-shadow: 0 0 20px rgb(255, 255, 255);
  }
  100% {
    text-shadow:
      0 0 20px rgb(255, 255, 255),
      0 0 30px rgb(255, 255, 255);
  }
}

@keyframes blink {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}
</style>
