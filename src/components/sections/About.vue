<script setup>
import Ticker from "./Ticker.vue";

const tech = [
  {
    name: "Vue.js",
    url: "https://vuejs.org",
    icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg",
  },
  {
    name: "Vite",
    url: "https://vite.dev/",
    icon: "https://www.svgrepo.com/show/374167/vite.svg",
  },
  {
    name: "JavaScript",
    url: "https://javascript.info",
    icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg",
  },
  {
    name: "Python",
    url: "https://python.org",
    icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg",
  },
  {
    name: "CSS",
    url: "https://en.wikipedia.org/wiki/CSS",
    icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg",
  },
  {
    name: "HTML",
    url: "https://en.wikipedia.org/wiki/HTML",
    icon: "https://www.svgrepo.com/show/452228/html-5.svg",
  },
  {
    name: "Discord.py",
    url: "https://discordpy.readthedocs.io/en/stable/",
    icon: "https://raw.githubusercontent.com/python-discord/branding/main/logos/logo_discord/logo_discord.svg",
  },
  {
    name: "Tailwindcss",
    url: "https://tailwindcss.com/",
    icon: "https://www.svgrepo.com/show/374118/tailwind.svg",
  },
];

const tools = [
  {
    name: "VSCode",
    url: "https://code.visualstudio.com",
    icon: "https://www.svgrepo.com/show/354522/visual-studio-code.svg",
  },
  {
    name: "Git",
    url: "https://git-scm.com",
    icon: "https://www.svgrepo.com/show/452210/git.svg",
  },
  {
    name: "Github",
    url: "https://github.com",
    icon: "https://www.svgrepo.com/show/512317/github-142.svg",
  },
  {
    name: "Nixos",
    url: "https://nixos.org/",
    icon: "https://www.svgrepo.com/show/373927/nix.svg",
  },
  {
    name: "Kali",
    url: "https://www.kali.org/",
    icon: "https://www.svgrepo.com/show/330767/kalilinux.svg",
  },
  {
    name: "Nmap",
    url: "https://nmap.org/",
    icon: "https://img.icons8.com/?size=96&id=9b5wowKIlo9d&format=png",
  },
];
</script>

<template>
  <div class="font-sans text-white">
    <h1 class="font-sans text-4xl font-extralight mb-2">About Me</h1>
    <p class="font-quicksand text-base text-white/30 mb-7">Who I am and what I do</p>
    <div class="flex flex-col gap-10">
      <div class="grid p-2 grid-cols-1 md:grid-cols-[24rem_1fr]">
        <div class="flex flex-col gap-1">
          <p class="about-label"><img src="@/assets/about/age.svg" class="about-label-img" />Age</p>
          <p class="about-value">~14 Years Old</p>
          <p class="about-label">
            <img src="@/assets/about/location.svg" class="about-label-img" />Location
          </p>
          <p class="about-value">Indonesia, Bogor</p>
          <p class="about-label">
            <img src="@/assets/about/roles.svg" class="about-label-img" />Roles
          </p>
          <p class="about-value">Discord Bot Dev - Frontend Dev - Pentester - Artist</p>
          <p class="about-label">
            <img src="@/assets/about/motto.svg" class="about-label-img" />Motto
          </p>
          <p class="about-value">L'Art du Savoir</p>
        </div>

        <div class="flex flex-col gap-2 mt-8 md:mt-0">
          <div class="flex flex-col gap-0.5">
            <p class="text-lg text-white/90 font-light">
              Hi! I'm Fel, also known as Aarch or Archie — a
              <span class="font-medium">Programmer</span>,
              <span class="font-medium">Pentester</span>, and an
              <span class="font-medium">Artist</span>, who loves exploring everything. I'm still
              learning Javascript Vue.js, and my goals is to learn as much as possible until I
              master everything.
            </p>
          </div>

          <hr class="border-t border-white/5" />

          <div>
            <p class="text-lg text-white/60 font-light">
              I believe <span class="underline">learning is an art in itself</span>. I build things
              — from web apps to bots, and sometimes I draw too. I started learning in 2022, and now
              I'm still learning
            </p>
          </div>
        </div>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-[1fr_12rem_18rem] gap-4">
        <div class="about-sub-card">
          <p class="about-label">
            <img src="@/assets/about/tools.svg" class="about-label-img" />Technologies I used
          </p>
          <Ticker :items="tech" :dur="10" />

          <p class="about-label mt-6">
            <img src="@/assets/about/tools.svg" class="about-label-img" />Tools I used
          </p>
          <Ticker :items="tools" :dur="8" />
        </div>
        <div class="about-sub-card">
          <p class="about-label">
            <img src="@/assets/about/hobby.svg" class="about-label-img" />Hobbies
          </p>
          <p class="about-value">Programming</p>
          <p class="about-value">Learning</p>
          <p class="about-value">Drawing</p>
          <p class="about-value">Gaming</p>
          <p class="about-value">Music</p>
        </div>
        <div class="about-sub-card">
          <p class="about-label">
            <img src="@/assets/about/experience.svg" class="about-label-img" />Experience
          </p>
          <p class="about-value">~ 3 Years in Development</p>
          <p class="about-value">~ 3 Years as a Digital Artist</p>
          <p class="about-value">~ 1 Years as a Discord Bot Developer</p>
          <p class="about-value">~ 1 Years as a Frontend Developer</p>
        </div>
      </div>
    </div>
  </div>
</template>
