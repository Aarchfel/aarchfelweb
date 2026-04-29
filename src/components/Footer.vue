<template>
  <footer
    class="font-sans relative overflow-hidden border border-t-white/5 bg-radial-[ellipse_at_15%_40%] from-white/3 to-transparent to-60% py-4 px-[19%] backdrop-blur-md"
  >
    <div class="text-white flex item-start justify-between gap-0">
      <div class="flex flex-col gap-0.2">
        <span class="font-quicksand text-white/90 text-base font-normal">Aarchfel</span>
        <span class="text-xs text-white/50">
          Discord Bot Dev · Frontend Dev · Pentester · Artist
        </span>
        <span class="text-medium mt-2 font-light text-white/50">
          Built with love and desperation and support from nothing.
        </span>
        <span class="text-xs text-white/20 mt-9">© 2026 aarchfel. All rights reserved.</span>
      </div>
      <div class="flex flex-col items-end gap-3">
        <div class="flex gap-4">
          <a
            href="#home"
            class="text-sm text-white/35 transition-colors duration-200 ease-in hover:text-white cursor-pointer"
          >
            Home
          </a>
          <a
            href="#about"
            class="text-sm text-white/35 transition-colors duration-200 ease-in hover:text-white cursor-pointer"
          >
            About
          </a>
          <a
            href="#projects"
            class="text-sm text-white/35 transition-colors duration-200 ease-in hover:text-white cursor-pointer"
          >
            Projects
          </a>
          <a
            href="#contact"
            class="text-sm text-white/35 transition-colors duration-200 ease-in hover:text-white cursor-pointer"
          >
            Contact
          </a>
        </div>
        <div class="socials">
          <a href="https://github.com/aarchfel" target="_blank" class="group cursor-pointer">
            <img
              src="@/assets/footer/github.svg"
              alt="Github"
              class="opacity-50 transition-all duration-200 group-hover:opacity-100 w-8 h-8"
            />
          </a>
        </div>
      </div>
    </div>
    <hr class="border-t-white/5 mt-5 mb-4" />
    <div class="flex items-center justify-between">
      <span class="text-xs text-white/15 italic">L'Art du Savoir</span>
      <a
        href="https://github.com/Aarchfel/aarchfelweb"
        target="_blank"
        class="group text-xs inline-flex items-center gap-1 text-white/20 transition-colors duration-200 hover:text-white cursor-pointer"
      >
        Website Source Code
        <img
          src="@/assets/footer/source.svg"
          alt="Source Code"
          class="w-4 h-4 opacity-20 transition-opacity duration-200 group-hover:opacity-100"
        />
      </a>
    </div>
  </footer>
</template>
