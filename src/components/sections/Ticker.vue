<script setup>
import { ref, computed, onMounted, onUnmounted } from "vue";

defineProps({
  items: Array,
  dur: { type: Number, default: 18 },
});

const cRef = ref(null);
const sRef = ref(null);
const repeat = ref(2);

function recalc() {
  if (!cRef.value || !sRef.value) return;
  const cw = cRef.value.offsetWidth;
  const sw = sRef.value.offsetWidth;
  if (sw === 0) return;
  repeat.value = Math.max(2, Math.ceil(cw / sw) + 2);
}

let ro;
onMounted(() => {
  ro = new ResizeObserver(recalc);
  if (cRef.value) ro.observe(cRef.value);
  recalc();
});
onUnmounted(() => ro?.disconnect());
const shift = computed(() => `-${100 / repeat.value}%`);
</script>

<template>
  <div ref="cRef" class="relative overflow-hidden w-full">
    <div
      class="flex w-max animate-ticker hover:[animation-play-state:paused]"
      :style="{ '--dur': `${dur}s`, '--shift': shift }"
    >
      <div
        v-for="i in repeat"
        :key="i"
        :ref="
          (el) => {
            if (i === 1) sRef = el;
          }
        "
        class="flex gap-2.5 pr-2.5"
      >
        <a
          v-for="item in items"
          :key="`${i}-${item.name}`"
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
