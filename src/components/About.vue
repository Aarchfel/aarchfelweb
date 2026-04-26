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
];
</script>

<template>
  <div>
    <h1>About Me</h1>
    <p>Who I am and what I do</p>
    <div class="cards-wrap">
      <div class="main-grid">
        <div class="left-sect">
          <p class="label"><img src="@/assets/about/age.svg" />Age</p>
          <p class="value">~14 Years Old</p>
          <p class="label"><img src="@/assets/about/location.svg" />Location</p>
          <p class="value">Indonesia, Bogor</p>
          <p class="label"><img src="@/assets/about/roles.svg" />Roles</p>
          <p class="value">Discord Bot Dev - Frontend Dev - Pentester - Artist</p>
          <p class="label"><img src="@/assets/about/motto.svg" />Motto</p>
          <p class="value">L'Art du Savoir</p>
        </div>

        <div class="div-v" />

        <div class="right-sect">
          <div class="right-top">
            <p class="value sm">
              Hi! I'm Fel, also known as Aarch or Archie — a programmer, pentester, and artist who
              loves exploring everything. I'm still learning Javascript Vue.js, and my goals is to
              learn as much as possible until I master everything.
            </p>
          </div>

          <hr />

          <div class="right-bottom">
            <p class="text">
              I believe learning is an art in itself. I build things — from web apps to bots, and
              sometimes I draw too. I started learning in 2022, and now I'm still learning
            </p>
          </div>
        </div>
      </div>

      <div class="sub-grid">
        <div class="sub-card">
          <p class="label"><img src="@/assets/about/tools.svg" />Technologies I used</p>
          <Ticker :items="tech" :dur="10" />

          <p class="label" style="margin-top: 2.5rem">
            <img src="@/assets/about/tools.svg" />Tools I used
          </p>
          <Ticker :items="tools" :dur="8" />
        </div>
        <div class="sub-card">
          <p class="label"><img src="@/assets/about/hobby.svg" />Hobbies</p>
          <p class="valuec">Programming</p>
          <p class="valuec">Learning</p>
          <p class="valuec">Drawing</p>
          <p class="valuec">Gaming</p>
          <p class="valuec">Music</p>
        </div>
        <div class="sub-card">
          <p class="label"><img src="@/assets/about/experience.svg" />Experience</p>
          <p class="valuec">~ 3 Years in Development</p>
          <p class="valuec">~ 3 Years as a Digital Artist</p>
          <p class="valuec">~ 1 Years as a Discord Bot Developer</p>
          <p class="valuec">~ 1 Years as a Frontend Developer</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1,
h2,
h3 {
  font-family: "DM Sans", sans-serif;
}

body,
p,
a,
span {
  font-family: "Inter", sans-serif;
  font-weight: 280;
}

.cards-wrap {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 2rem 0.2rem;
}

.main-grid {
  background: transparent;
  border: 0px solid rgba(255, 255, 255, 0.08);
  border-radius: 5px;
  padding: 0.3rem;
  display: grid;
  grid-template-columns: 1fr 1px 1fr;
  gap: 0.5rem;
}

.div-v {
  background: rgba(255, 255, 255, 0.08);
}

.right-sect {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.right-top {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

hr {
  border: none;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.right-bottom {
  padding-top: 0.1em;
}

.sub-grid {
  display: grid;
  margin-top: 3%;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.3rem;
}

.sub-card {
  background: transparent;
  border: 0px solid rgba(255, 255, 255, 0.08);
  border-radius: 5px;
  padding: 0.1em;
  min-width: 0;
  overflow: hidden;
}

.label {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.35);
  margin: 0 0 5px;
}

h1 {
  font-size: 2em;
  font-weight: 200;
  margin-bottom: 0.23rem;
}

p {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.35);
  display: flex;
  align-items: center;
  gap: 6px;
}

p img {
  width: 1rem;
  height: 1rem;
  opacity: 0.35;
}

.text {
  font-size: 1.17em;
  color: rgba(255, 255, 255, 0.65);
  margin: 0 0.4em 4px;
}

.value {
  font-size: 1.1em;
  font-weight: 300;
  color: white;
  margin: 0 0.4em 4px;
  margin-bottom: 1em;
}

.valuec {
  font-size: 1.1em;
  font-weight: 200;
  color: white;
  margin: 0 0.35em 3px;
}

.value.sm {
  font-size: 1.17em;
}
</style>
