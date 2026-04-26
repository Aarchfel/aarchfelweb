<template>
  <footer>
    <div class="inner">
      <div class="left">
        <span class="name">Aarchfel</span>
        <span class="sub">Discord Bot Dev · Frontend Dev · Pentester · Artist</span>
        <span class="desc">Built with love and desperation and support from nothing.</span>
        <span class="copy">© 2026 aarchfel. All rights reserved.</span>
      </div>
      <div class="right">
        <div class="links">
          <a href="#home">Home</a>
          <a href="#about">About</a>
          <a href="#projects">Projects</a>
          <a href="#contact">Contact</a>
        </div>
        <div class="socials">
          <a href="https://github.com/aarchfel" target="_blank">
            <img src="@/assets/footer/github.svg" alt="Github" />
          </a>
        </div>
      </div>
    </div>
    <hr />
    <div class="bottom">
      <span class="motto">L'Art du Savoir</span>
      <a href="#" class="src">
        Website Source Code <img src="@/assets/footer/source.svg" alt="Source Code" />
      </a>
    </div>
  </footer>
</template>

<style scoped>
h1,
h2,
h3 {
  font-family: "Nunito", sans-serif;
}

body,
p,
a,
span {
  font-family: "Montserrat", sans-serif;
  font-weight: 250;
}

footer {
  position: relative;
  overflow: hidden;
  background:
    radial-gradient(ellipse at 15% 40%, rgba(255, 255, 255, 0.02) 0%, transparent 60%),
    radial-gradient(ellipse at 85% 80%, rgba(255, 255, 255, 0.01) 0%, transparent 60%),
    rgba(255, 255, 255, 0.001);
  backdrop-filter: blur(12px);
  border-top: 1px solid rgba(255, 255, 255, 0.07);
  padding: 2rem 19%;
  padding-bottom: 1em;
}

.inner {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 2rem;
}

.left {
  display: flex;
  flex-direction: column;
  gap: 0.1rem;
}

.name {
  font-size: 1rem;
  font-weight: 330;
  color: white;
}

.sub {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.35);
}

.desc {
  font-size: 0.9rem;
  margin-top: 0.5em;
  color: rgba(255, 255, 255, 0.5);
}

.copy {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.2);
  margin-top: 2.5rem;
}

.right {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 1.4rem;
}

.links,
.socials {
  display: flex;
  gap: 1.15rem;
}

.links a,
.socials a {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.35);
  text-decoration: none;
  transition: color 0.2s ease;
}

.links a:hover,
.socials a:hover {
  color: white;
}

.socials a img {
  width: 2rem;
  height: 2rem;
}

hr {
  border: none;
  border-top: 0.5px solid rgba(255, 255, 255, 0.06);
  margin: 1.25rem 0 1rem;
}

.bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.motto {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.15);
  font-style: italic;
}

.src {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.2);
  text-decoration: none;
  transition: color 0.2s ease;
  display: inline-flex;
  align-items: center;
  gap: 4px;
}

.src img {
  width: 1em;
  height: 1em;
  opacity: 0.2;
  transition: opacity 0.2s ease;
}

.src:hover {
  color: rgba(255, 255, 255, 0.5);
}

.src:hover img {
  opacity: 0.5;
}
</style>
