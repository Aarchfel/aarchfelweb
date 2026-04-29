<template>
  <div class="font-sans text-white">
    <h1 class="font-quicksand text-4xl font-extralight mb-2">Contacts</h1>
    <p class="font-quicksand text-base text-white/30 mb-7">
      Feel free to reach out and talk with me
    </p>
    <div class="grid grid-cols-[1fr_1px_20rem] gap-3">
      <div class="flex flex-col">
        <p class="text-base text-white/70 font-normal mb-3">
          Feel free to talk me, I'm always open to talk — whether it's about code, art, security, or
          just anything random.
        </p>
        <p class="text-base text-white/70 font-light">Best way to reach me is Discord or Email.</p>
      </div>

      <div class="w-px h-full min-h-25 bg-white/10"></div>

      <div class="flex flex-col gap-2">
        <a href="mailto:aarchfel@gmail.com" class="flex items-center w-fit group">
          <img
            src="@/assets/contact/gmail.svg"
            class="w-10 mr-2 opacity-50 transition-opacity duration-200 group-hover:opacity-100"
          />
          <div class="flex flex-col">
            <span
              class="font-heading text-white/30 font-light text-sm mb-0.2 leading-none transition-colors duration-200 group-hover:text-white/50"
            >
              Gmail
            </span>
            <span
              class="quicksand-font text-md text-white/50 leading-none transition-colors duration-200 group-hover:text-white"
            >
              aarchfel@gmail.com
            </span>
          </div>
        </a>
        <a
          href="https://discord.com/users/1144160512586809384/"
          target="_blank"
          class="flex items-center w-fit group"
        >
          <img
            src="@/assets/contact/discord.svg"
            class="w-10 mr-2 opacity-50 transition-opacity duration-200 group-hover:opacity-100"
          />
          <div class="flex flex-col">
            <span
              class="font-heading text-white/30 font-light text-sm mb-0.2 leading-none transition-colors duration-200 group-hover:text-white/50"
            >
              Discord
            </span>
            <span
              class="quicksand-font text-md text-white/50 leading-none transition-colors duration-200 group-hover:text-white"
            >
              aarchfel</span
            >
          </div>
        </a>
        <a
          href="https://github.com/aarchfel"
          target="_blank"
          class="flex items-center w-fit group cursor-pointer"
        >
          <img
            src="@/assets/contact/github.svg"
            class="w-10 mr-2 opacity-50 transition-opacity duration-200 group-hover:opacity-100"
          />
          <div class="flex flex-col">
            <span
              class="font-heading text-white/30 font-light text-sm mb-0.2 leading-none transition-colors duration-200 group-hover:text-white/50"
            >
              Github
            </span>
            <span
              class="quicksand-font text-md text-white/50 leading-none transition-colors duration-200 group-hover:text-white"
            >
              @aarchfel
            </span>
          </div>
        </a>
        <a
          href="https://www.tiktok.com/@aarchxyz"
          target="_blank"
          class="flex items-center w-fit group"
        >
          <img
            src="@/assets/contact/tiktok.svg"
            class="w-10 mr-2 opacity-50 transition-opacit duration-200 group-hover:opacity-100"
          />
          <div class="flex flex-col">
            <span
              class="font-heading text-white/30 font-light text-sm mb-0.2 leading-none transition-colors duration-200 group-hover:text-white/50"
            >
              Tiktok
            </span>
            <span
              class="quicksand-font text-md text-white/50 leading-none transition-colors duration-200 group-hover:text-white"
            >
              @aarchxyz
            </span>
          </div>
        </a>
      </div>
    </div>
  </div>
</template>
