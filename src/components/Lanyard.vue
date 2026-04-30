<script setup>
import { useLanyard } from "@leonardssh/use-lanyard";
import { computed, onMounted, ref } from "vue";

const rpc = ref(null);
const isVis = ref(true);
let timer = null;

useLanyard({
  userId: "1144160512586809384",
  socket: true,
  onPresenceUpdate: (data) => {
    rpc.value = data;
  },
});

const vcodeAct = computed(() => {
  return rpc.value?.activities?.find((a) => a.name === "Code");
});

const vcodeImg = computed(() => {
  if (!vcodeAct.value || !vcodeAct.value.assets) return null;

  if (vcodeAct.value.assets.large_image.includes("external")) {
    return `https://media.discordapp.net/external/${vcodeAct.value.assets.large_image.split("mp:external/")[1]}`;
  }
  return `https://cdn.discordapp.com/app-assets/${vcodeAct.value.application_id}/${vcodeAct.value.assets.large_image}.png`;
});

const hasActivity = computed(() => {
  const isSpotify = rpc.value?.listening_to_spotify;
  const isVscode = !!vcodeAct.value;
  return isSpotify || isVscode;
});

const statCol = computed(() => {
  const stats = rpc.value?.discord_status;
  if (stats === "online") return "bg-green-700";
  if (stats === "dnd") return "bg-red-900";
  if (stats === "idle") return "bg-yellow-900";
  return "bg-gray-700";
});

const sTimer = () => {
  clearTimeout(timer);
  timer = setTimeout(() => (isVis.value = false), 2000);
};

const showB = () => {
  clearTimeout(timer);
  isVis.value = true;
};

onMounted(() => sTimer());
</script>

<template>
  <div
    v-if="hasActivity"
    class="hidden md:block font-sans fixed bottom-0 left-0 z-999 transition-transform duration-500 ease-in-out"
    :class="isVis ? 'translate-y-0' : 'translate-y-[calc(100%-10px)]'"
    @mouseenter="showB"
    @mouseleave="sTimer"
  >
    <div
      class="w-70 bg-neutral-900/90 border border-white/5 rounded-tr-xl p-2 shadow-sm text-white"
    >
      <div class="flex items-center gap-2 mb-2 pb-2 border-b border-white/5">
        <div class="relative">
          <img
            :src="`https://cdn.discordapp.com/avatars/${rpc?.discord_user.id}/${rpc?.discord_user.avatar}.png`"
            class="w-10 h-10 rounded-full border border-neutral-800"
          />
          <div :class="statCol" class="absolute bottom-0 right-0 p-1.5 rounded-full"></div>
        </div>
        <div class="flex flex-col">
          <span class="text-sm font-heading leading-none mb-0.5">{{
            rpc?.discord_user.username
          }}</span>
          <span class="text-[12px] text-white/30 leading-none">
            {{ rpc?.discord_status }}
          </span>
        </div>
      </div>

      <div class="space-y-2">
        <div v-if="vcodeAct" class="flex items-center gap-2 bg-blue-800/10 p-1.5 rounded-xs">
          <img v-if="vcodeImg" :src="vcodeImg" class="w-12 h-12 rounded-md object-cover" />
          <div class="flex flex-col overflow-hidden">
            <span class="text-[9px] text-blue-500 font-sans font-bold uppercase">
              Visual Studio Code
            </span>
            <span class="text-white/80 text-xs truncate font-quicksand font-medium">
              {{ vcodeAct.details }}
            </span>
            <span class="text-[10px] text-slate-400 truncate">{{ vcodeAct.state }}</span>
          </div>
        </div>

        <div
          v-if="rpc?.listening_to_spotify"
          class="flex items-center gap-2 bg-green-950/20 p-1.5 rounded-xs"
        >
          <img :src="rpc.spotify.album_art_url" class="w-12 h-12 rounded-xs shadow-lg" />
          <div class="flex flex-col overflow-hidden">
            <span class="text-[9px] text-green-500 font-sans font-bold uppercase">
              Listening to Spotify
            </span>
            <span class="text-white/80 text-xs truncate font-quicksand font-medium">
              {{ rpc.spotify.song }}
            </span>
            <span class="text-[10px] text-slate-400 truncate">by {{ rpc.spotify.artist }}</span>
          </div>
        </div>

        <div
          v-if="!vcodeAct && !rpc?.listening_to_spotify"
          class="text-center py-2 text-[10px] text-neutral-500 italic"
        >
          Not doing anything yet...
        </div>
      </div>
    </div>
  </div>
</template>
