<script setup>
import Profile from "@/components/Profile.vue";
import About from "@/components/About.vue";
import Project from "@/components/Projects.vue";
import { onMounted } from "vue";
import Footer from "@/components/Footer.vue";

onMounted(() => {
  const sect = document.querySelectorAll(".sect-anim");

  const observ = new IntersectionObserver(
    (entr) => {
      entr.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("visible");
        }
      });
    },
    { threshold: 0.1 },
  );

  sect.forEach((sect) => observ.observe(sect));

  const hashsect = document.querySelectorAll("section[id]");
  const hashobserv = new IntersectionObserver(
    (ent) => {
      ent.forEach((ent) => {
        if (ent.isIntersecting) {
          history.replaceState(null, "", `#${ent.target.id}`);
        }
      });
    },
    { threshold: 0.5 },
  );
  hashsect.forEach((sect) => hashobserv.observe(sect));
});
</script>

<template>
  <main>
    <section id="home" class="hero sect-anim">
      <img src="@/assets/background.png" />
      <Profile />
    </section>

    <section id="about" class="about sect-anim">
      <About />
    </section>

    <section id="projects" class="projects sect-anim">
      <Project />
    </section>

    <section id="contact" class="contact sect-anim">
      <h2 style="font-size: 2em; font-weight: 500; margin-bottom: 0.23rem">Contact</h2>
      <p style="font-size: 0.9rem; color: rgba(255, 255, 255, 0.35); margin-bottom: 2rem">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorem dolorum, debitis laudantium
        fugiat, tenetur dignissimos iure officia quaerat, sed qui modi pariatur quidem harum ratione
        iusto in. Doloremque, accusantium tempora?
      </p>
      <p style="font-size: 0.9rem; color: rgba(255, 255, 255, 0.35); margin-bottom: 2rem">
        Coming soon..
      </p>
    </section>
  </main>
  <Footer />
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

.hero {
  min-height: 125vh;
  position: relative;
  overflow: hidden;
  background:
    radial-gradient(ellipse at 55% 60%, rgba(255, 255, 255, 0.25) 4%, transparent 60%),
    radial-gradient(ellipse at 55% 40%, rgba(101, 22, 161, 0.19) 0%, transparent 50%),
    rgb(23, 23, 23);
}

.hero > img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  opacity: 0.12;
  z-index: 0;
}

.hero > :not(img) {
  position: relative;
  z-index: 1;
}

.hero::after {
  z-index: 2;
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 280px;
  background: linear-gradient(to bottom, transparent, rgb(23, 23, 23));
  pointer-events: none;
}

.about,
.projects,
.contact {
  min-height: 100vh;
  background: rgb(23, 23, 23);
  color: white;
  padding: 12vh 18%;
}

.sect-anim {
  opacity: 0;
  transform: translateY(30px);
  transition:
    opacity 1s ease,
    transform 1s ease;
}

.sect-anim.visible {
  opacity: 1;
  transform: translateY(0);
}
</style>
