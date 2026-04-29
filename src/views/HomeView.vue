<script setup>
import Profile from "@/components/sections/Profile.vue";
import About from "@/components/sections/About.vue";
import Project from "@/components/sections/Projects.vue";
import { onMounted } from "vue";
import Footer from "@/components/Footer.vue";
import Contact from "@/components/sections/Contact.vue";
import Lanyard from "@/components/Lanyard.vue";

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
  <Lanyard />
  <main class="bg-neutral-900">
    <section
      id="home"
      class="relative min-h-[120vh] flex justify-center overflow-hidden bg-hero-pattern after:content-[''] after:absolute after:bottom-0 after:left-0 after:right-0 after:h-72 after:bg-linear-to-b after:from-transparent after:to-neutral-900 after:pointer-events-none after:z-20"
    >
      <img
        src="@/assets/background.png"
        class="absolute inset-0 w-full h-full object-cover opacity-12 z-0"
      />
      <Profile class="relative z-1" />
    </section>

    <section id="about" class="sect-anim min-h-screen bg-neutral-900 py-25 px-[35vh]">
      <About />
    </section>

    <section id="projects" class="sect-anim min-h-screen bg-neutral-900 py-25 px-[35vh]">
      <Project />
    </section>

    <section id="contact" class="sect-anim min-h-screen bg-neutral-900 py-25 px-[35vh]">
      <Contact />
    </section>
  </main>
  <Footer />
</template>

<style scoped>
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
  transform: translateY(50px);
  transition:
    opacity 1.2s ease,
    transform 1.2s ease;
}

.sect-anim.visible {
  opacity: 1;
  transform: translateY(0);
}
</style>
