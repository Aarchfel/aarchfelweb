<script setup>
import { ref, computed, onMounted } from "vue";
const reps = ref(null);

const sorted = computed(() =>
  reps.value?.toSorted((af, bef) => bef.stargazers_count - af.stargazers_count).slice(0, 6),
);

onMounted(() => {
  fetch("https://api.github.com/users/aarchfel/repos?per_page=99")
    .then((resp) => resp.json())
    .then((data) => (reps.value = data.filter((r) => !r.fork)));
});
</script>

<template>
  <section id="projects">
    <h1>My Projects</h1>
    <p>Here are my works and public repositories, sorted by stars</p>

    <div v-if="!sorted">Loading...</div>

    <div v-else class="grid">
      <div class="card" v-for="repo in sorted" :key="repo.id">
        <div class="thumbnail">
          <img
            :src="`https://opengraph.githubassets.com/1/${repo.owner.login}/${repo / name}`"
            :alt="repo.name"
            @error="(err) => (err.target.style.display = 'none')"
          />
          <div class="thumbnail-fb">
            <span>{{ repo.name }}</span>
          </div>
        </div>
        <div class="top">
          <a :href="repo.html_url" target="_blank" rel="noopener">{{ repo.name }}</a>
          <span class="lang" v-if="repo.language">{{ repo.language }}</span>
        </div>
        <p class="desc">{{ repo.description ?? "No description." }}</p>
        <div class="bottom">
          <span>★ {{ repo.stargazers_count }}</span>
          <span>⑂ {{ repo.forks_count }}</span>
        </div>
      </div>
    </div>
    <p style="margin-top: 2rem">
      More on my github: <a href="https://github.com/Aarchfel" target="_blank">Aarchfel</a>
    </p>
  </section>
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

section {
  background: rgb(23, 23, 23);
  color: white;
}

h1 {
  font-size: 2em;
  font-weight: 300;
  margin-bottom: 0.23rem;
}

p {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.35);
  margin-bottom: 2rem;
}

p a {
  text-decoration: none;
  color: white;
  font-size: 1rem;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 0.45rem;
}

.card {
  background: rgba(255, 255, 255, 0.008);
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  padding: 0;
  gap: 0;
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.card:hover {
  transform: scale(1.02);
  box-shadow: 0 0 16px rgba(255, 255, 255, 0.05);
}

.thumbnail {
  width: 100%;
  height: 140px;
  overflow: hidden;
  border-radius: 4px 4px 0 0;
  position: relative;
}

.thumbnail img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  position: relative;
  z-index: 1;
  display: block;
  filter: blur(4px);
  transition: filter 0.3s ease;
}

.thumbnail::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 15%;
  background: linear-gradient(to top, rgba(255, 255, 255, 0.04), transparent);
  z-index: 2;
  pointer-events: none;
}

.card:hover .thumbnail img {
  filter: blur(0);
}

.thumbnail-fb {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.03);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.thumbnail-fb span {
  font-size: 2rem;
  color: rgba(255, 255, 255, 0.2);
}

.top,
.desc,
.bottom {
  padding: 0 0.7rem;
}

.top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  padding-top: 1rem;
}

.top a {
  font-size: 0.95rem;
  font-weight: 350;
  color: white;
  text-decoration: none;
}

.top a:hover {
  text-decoration: underline;
  text-underline-offset: 3px;
}

.lang {
  font-size: 0.8rem;
  padding: 3px 12px;
  border-radius: 5px;
  background: rgba(255, 255, 255, 0.04);
  color: rgba(255, 255, 255, 0.85);
  border: 1px solid rgba(255, 255, 255, 0.06);
  white-space: nowrap;
  flex-shrink: 0;
}

.desc {
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.4);
  line-height: 2.1em;
  flex: 1;
}

.bottom {
  display: flex;
  gap: 20px;
  padding-bottom: 0.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.06);
  margin-top: 6px;
}

.bottom span {
  font-size: 0.9rem;
  padding-top: 0.5rem;
  color: rgba(255, 255, 255, 0.3);
}

.bottom span:first-child {
  color: rgba(255, 255, 255, 0.8);
}
</style>
