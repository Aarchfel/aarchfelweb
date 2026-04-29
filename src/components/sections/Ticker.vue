<script setup>
defineProps({
  items: Array,
  dur: { type: Number, default: 18 },
});
</script>

<template>
  <div class="relative overflow-hidden w-full">
    <div
      class="flex w-max animate-ticker hover:[animation-play-state:paused]"
      :style="{ '--dur': `${dur}s` }"
    >
      <div class="flex gap-2.5 pr-2.5">
        <a
          v-for="item in items"
          :key="item.name"
          :href="item.url"
          target="_blank"
          rel="noopener"
          class="ticker-badge"
        >
          <img :src="item.icon" class="ticker-badge-img" />
          {{ item.name }}
        </a>
      </div>
      <div class="flex gap-2.5 pr-2.5">
        <a
          v-for="item in items"
          :key="'dup-' + item.name"
          :href="item.url"
          target="_blank"
          rel="noopener"
          class="ticker-badge"
        >
          <img :src="item.icon" class="ticker-badge-img" />
          {{ item.name }}
        </a>
      </div>
    </div>
    <div
      class="absolute top-0 bottom-0 left-0 w-10 z-10 pointer-events-none bg-linear-to-r from-neutral-900 to-transparent"
    />
    <div
      class="absolute top-0 bottom-0 right-0 w-10 z-10 pointer-events-none bg-linear-to-l from-neutral-900 to-transparent"
    />
  </div>
</template>
