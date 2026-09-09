<script setup lang="ts">
import { bran } from '../data/bran'

const avatarSrc = `${import.meta.env.BASE_URL}bran-avatar.jpeg`
const symbolSrc = `${import.meta.env.BASE_URL}bran-symbol.jpeg`
</script>

<template>
  <header id="hero" class="hero">
    <img
      class="hero__image"
      :src="avatarSrc"
      :alt="`${bran.name} — дварф с капюшоном и родовым бочонком`"
      width="1024"
      height="1024"
    />
    <div class="hero__scrim" aria-hidden="true" />
    <div class="hero__copy reveal">
      <img class="hero__crest" :src="symbolSrc" alt="Родовой знак «Хмельная монета»" width="72" height="72" />
      <p class="hero__brand">{{ bran.name }}</p>
      <p class="hero__tag">{{ bran.tagline }}</p>
      <p class="hero__hook">{{ bran.hook }}</p>
      <a class="hero__cta" href="#who">К листу и шпаргалке</a>
    </div>
  </header>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 100svh;
  min-height: 100dvh;
  display: grid;
  align-items: end;
  overflow: hidden;
  background: var(--olive-deep);
}

.hero__image {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center 18%;
}

.hero__scrim {
  position: absolute;
  inset: 0;
  background:
    linear-gradient(180deg, rgba(26, 18, 12, 0.15) 0%, rgba(26, 18, 12, 0.2) 35%, rgba(26, 18, 12, 0.92) 100%),
    linear-gradient(90deg, rgba(26, 18, 12, 0.45), transparent 55%);
  animation: glow 4s ease-in-out infinite alternate;
}

@keyframes glow {
  from {
    filter: brightness(1);
  }
  to {
    filter: brightness(1.06);
  }
}

.hero__copy {
  position: relative;
  z-index: 1;
  padding: clamp(1.5rem, 6vw, 3rem) var(--pad) clamp(2.5rem, 8vw, 4rem);
  max-width: 36rem;
  animation: rise 0.9s ease both;
}

.hero__crest {
  display: block;
  width: 4.5rem;
  height: 4.5rem;
  margin: 0 0 0.85rem;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
}

.hero__brand {
  margin: 0 0 0.65rem;
  font-family: var(--font-display);
  font-size: clamp(2.1rem, 8.5vw, 3.4rem);
  font-weight: 700;
  line-height: 1.05;
  color: var(--foam);
  text-shadow: 0 2px 18px rgba(0, 0, 0, 0.45);
}

.hero__tag {
  margin: 0 0 0.85rem;
  font-size: 0.95rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: var(--amber-bright);
}

.hero__hook {
  margin: 0 0 1.35rem;
  color: var(--foam-dim);
  font-size: 1.05rem;
  max-width: 28rem;
}

.hero__cta {
  display: inline-block;
  padding: 0.7rem 1.15rem;
  background: var(--amber);
  color: var(--ink);
  font-weight: 700;
  text-decoration: none;
  border-radius: var(--radius);
  transition: transform 0.2s ease, background 0.2s ease;
}

.hero__cta:hover {
  background: var(--amber-bright);
  color: var(--ink);
  transform: translateY(-1px);
}

@media (min-width: 768px) {
  .hero__image {
    object-position: center 22%;
  }

  .hero__copy {
    max-width: 40rem;
  }
}
</style>
