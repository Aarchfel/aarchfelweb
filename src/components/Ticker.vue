<script setup>
defineProps({
  items: Array,
  dur: { type: Number, default: 18 },
});
</script>

<template>
  <div class="t-inner">
    <div class="t-track" :style="{ animationDuration: dur + 's' }">
      <div class="t-set">
        <a
          v-for="item in items"
          :key="item.name"
          :href="item.url"
          target="_blank"
          rel="noopener"
          class="badge"
        >
          <img :src="item.icon" />
          {{ item.name }}
        </a>
      </div>
      <div class="t-set" aria-hidden="true">
        <a
          v-for="item in items"
          :key="'dup-' + item.name"
          :href="item.url"
          target="_blank"
          rel="noopener"
          class="badge"
        >
          <img :src="item.icon" />
          {{ item.name }}
        </a>
      </div>
    </div>
    <div class="fade-l" />
    <div class="fade-r" />
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
  font-weight: 350;
}

.t-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}

.t-track {
  display: flex;
  width: max-content;
  animation: ticker linear infinite;
}

.t-track:hover {
  animation-play-state: paused;
}

.t-set {
  display: flex;
  gap: 10px;
  padding-right: 10px;
}

.badge {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  font-size: 0.8rem;
  padding: 0.45rem 0.7rem;
  border-radius: 5px;
  background: rgba(255, 255, 255, 0.03);
  color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(255, 255, 255, 0.1);
  text-decoration: none;
  white-space: nowrap;
  transition:
    background 0.2s ease,
    transform 0.3s ease;
}

.badge:hover {
  background: rgba(255, 255, 255, 0.22);
  transform: scale(1.05);
}

.badge img {
  width: 0.8rem;
  height: 0.8rem;
  object-fit: contain;
}

.fade-l,
.fade-r {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 40px;
  pointer-events: none;
  z-index: 1;
}

.fade-l {
  left: 0;
  background: linear-gradient(to right, #171717 7%, transparent);
}

.fade-r {
  right: 0;
  background: linear-gradient(to left, #171717 7%, transparent);
}

@keyframes ticker {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}
</style>
