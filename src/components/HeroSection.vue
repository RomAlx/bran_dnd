<script setup lang="ts">
import { bran } from '../data/bran'

const avatarSrc = `${import.meta.env.BASE_URL}bran-avatar.jpeg`
const avatarWideSrc = `${import.meta.env.BASE_URL}bran-avatar-wide.jpeg`
const symbolSrc = `${import.meta.env.BASE_URL}bran-symbol.jpeg`
</script>

<template>
  <header id="hero" class="hero">
    <picture class="hero__media">
      <source :srcset="avatarWideSrc" media="(min-width: 768px)" />
      <img
        class="hero__image"
        :src="avatarSrc"
        :alt="`${bran.name} — дварф с капюшоном и родовым бочонком`"
        width="768"
        height="1376"
      />
    </picture>
    <div class="hero__scrim" aria-hidden="true" />
    <div class="hero__copy reveal">
      <img class="hero__crest" :src="symbolSrc" alt="Родовой знак «Хмельная монета»" width="88" height="88" />
      <p class="hero__brand">
        <span class="hero__brand-name">Бран</span>
        <span class="hero__brand-nick">«Пустая пинта»</span>
        <span class="hero__brand-name">Пенобород</span>
      </p>
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

.hero__media {
  position: absolute;
  inset: 0;
}

.hero__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center 35%;
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
  width: 5.5rem;
  height: 5.5rem;
  margin: 0 0 1rem;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
}

.hero__brand {
  margin: 0 0 0.65rem;
  display: flex;
  align-items: baseline;
  gap: 0.2em;
  flex-wrap: nowrap;
  white-space: nowrap;
  font-size: clamp(1.18rem, 4.8vw, 3.9rem);
  font-weight: 700;
  line-height: 1.05;
  color: var(--foam);
  text-shadow: 0 2px 18px rgba(0, 0, 0, 0.45);
}

.hero__brand-name {
  font-family: var(--font-body);
  letter-spacing: 0;
}

.hero__brand-nick {
  font-family: var(--font-display);
  font-size: 1.08em;
  color: var(--amber-bright);
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
    object-position: center 30%;
  }

  .hero__copy {
    max-width: 40rem;
  }

  .hero__brand {
    font-size: clamp(2.8rem, 4.8vw, 4.8rem);
    gap: 0.35em;
  }
}
</style>
