<script setup>
import { ref, computed, onMounted } from "vue";
const reps = ref(null);

const prevs = {
  "aarchfel.app":
    "https://raw.githubusercontent.com/Aarchfel/aarchfel.app/main/preview/aarchfel.app.jpg",
};

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
  <section class="font-sans text-white">
    <h1 class="font-quicksand text-4xl font-extralight mb-2">My Projects</h1>
    <p class="font-quicksand text-base text-white/30 mb-7">
      Here are my works and public repositories, sorted by stars
    </p>

    <div v-if="!sorted" class="text-white/20 italic">Loading...</div>

    <div v-else class="grid grid-cols-[repeat(auto-fill,minmax(250px,1fr))] gap-2">
      <div
        v-for="repo in sorted"
        :key="repo.id"
        class="group flex flex-col rounded-md bg-white/[0.008] border border-white/5 transition-all duration-300 ease-in-out hover:scale-[1.02] hover:shadow-[0_0_16px_rgba(255,255,255,0.02)] overflow-hidden"
      >
        <div class="relative w-full h-36 overflow-hidden bg-white/3">
          <div class="absolute inset-0 flex items-center justify-center p-4">
            <span class="text-white/10 text-xl font-bold truncate">{{ repo.name }}</span>
          </div>

          <img
            :src="
              prevs[repo.name] ||
              `https://opengraph.githubassets.com/1/${repo.owner.login}/${repo.name}`
            "
            :alt="repo.name"
            class="relative z-10 block w-full h-full object-cover blur-xs transition duration-500 ease-in-out group-hover:blur-none"
          />

          <div
            class="absolute bottom-0 left-0 right-0 h-1/3 z-2 bg-linear-to-t from-black/20 to-transparent pointer-events-none"
          ></div>
        </div>

        <div class="flex items-center justify-between gap-2 px-2 pt-1">
          <a
            :href="repo.html_url"
            target="_blank"
            rel="noopener"
            class="text-lg font-light text-white hover:underline decoration-white/10 underline-offset-4 transition-all"
          >
            {{ repo.name }}
          </a>
          <span
            v-if="repo.language"
            class="text-[10px] px-2 py-0.5 rounded-sm bg-white/5 text-white/60 border border-white/2 uppercase tracking-wider font-bold"
          >
            {{ repo.language }}
          </span>
        </div>

        <p class="flex-1 px-2 mt-3 text-sm text-white/30 line-clamp-2 min-h-10">
          {{ repo.description ?? "No description provided." }}
        </p>

        <div class="flex gap-4 px-4 py-3 mt-4 border-t border-white/5 bg-white/0.5">
          <span class="text-[0.8rem] text-white/70 flex items-center gap-1">
            <span class="text-white-500/80 text-xs">★</span> {{ repo.stargazers_count }}
          </span>
          <span class="text-[0.8rem] text-white/30 flex items-center gap-1">
            <span class="text-white/20 text-xs">⑂</span> {{ repo.forks_count }}
          </span>
        </div>
      </div>
    </div>

    <p class="mt-12 text-sm text-white/20">
      More on my github:
      <a
        href="https://github.com/Aarchfel"
        target="_blank"
        class="text-white/40 hover:text-white transition-colors underline decoration-white/10 underline-offset-4"
      >
        Aarchfel
      </a>
    </p>
  </section>
</template>
