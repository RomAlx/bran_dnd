<script setup lang="ts">
import { bran, fmtMod } from '../data/bran'
</script>

<template>
  <section id="stats" class="section stats">
    <div class="section__inner">
      <p class="section__eyebrow">Шесть характеристик</p>
      <h2 class="section__title">Что качает Брана</h2>
      <p class="section__lead">
        Модификатор идёт в броски. У Брана сильные Ловкость, Телосложение и Харизма.
      </p>

      <div class="abilities">
        <article v-for="ab in bran.abilities" :key="ab.key" class="ability">
          <header class="ability__head">
            <span class="ability__key">{{ ab.key }}</span>
            <span class="ability__score">{{ ab.score }}</span>
            <span class="ability__mod">{{ fmtMod(ab.mod) }}</span>
          </header>
          <h3>{{ ab.name }}</h3>
          <p>{{ ab.why }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.abilities {
  display: grid;
  gap: 0.85rem;
}

.ability {
  padding: 1rem 0;
  border-bottom: 1px solid var(--line);
}

.ability:last-child {
  border-bottom: none;
}

.ability__head {
  display: flex;
  align-items: baseline;
  gap: 0.65rem;
  margin-bottom: 0.35rem;
}

.ability__key {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  color: var(--amber-bright);
}

.ability__score {
  font-family: var(--font-display);
  font-size: 1.6rem;
  font-weight: 700;
}

.ability__mod {
  margin-left: auto;
  font-family: var(--font-display);
  font-size: 1.35rem;
  font-weight: 700;
  color: var(--amber-bright);
}

.ability h3 {
  font-size: 1.05rem;
  margin-bottom: 0.25rem;
}

.ability p {
  color: var(--foam-dim);
  font-size: 0.95rem;
}

@media (min-width: 640px) {
  .abilities {
    grid-template-columns: 1fr 1fr;
    gap: 0 1.5rem;
  }
}
</style>
