<script setup lang="ts">
import { bran } from '../data/bran'
</script>

<template>
  <section id="who" class="section who">
    <div class="section__inner">
      <p class="section__eyebrow">Персонаж</p>
      <h2 class="section__title">Кто такой Бран</h2>
      <p class="section__lead">{{ bran.personality.why }}</p>
      <blockquote class="who__meme">{{ bran.personality.meme }}</blockquote>

      <div class="who__traits">
        <p v-for="(trait, i) in bran.personality.traits" :key="i">{{ trait }}</p>
      </div>

      <div class="who__block">
        <h3>Внешность</h3>
        <p>{{ bran.personality.look }}</p>
      </div>

      <div class="who__block">
        <h3>За столом</h3>
        <p>{{ bran.personality.play }}</p>
      </div>

      <dl class="who__meta">
        <div>
          <dt>Раса</dt>
          <dd>{{ bran.race }}</dd>
        </div>
        <div>
          <dt>Класс</dt>
          <dd>{{ bran.className }} {{ bran.level }}</dd>
        </div>
        <div>
          <dt>Предыстория</dt>
          <dd>{{ bran.background }}</dd>
        </div>
        <div>
          <dt>Мировоззрение</dt>
          <dd>{{ bran.alignment }}</dd>
        </div>
        <div>
          <dt>Игрок</dt>
          <dd>{{ bran.player }}</dd>
        </div>
        <div>
          <dt>Опыт</dt>
          <dd>{{ bran.xp }} · ур. {{ bran.level }}</dd>
        </div>
      </dl>
      <p class="who__deity">{{ bran.deity }}</p>
    </div>
  </section>
</template>

<style scoped>
.who__traits {
  margin: 0 0 1.75rem;
  padding: 0.15rem 0 0.15rem 1rem;
  border-left: 3px solid var(--amber);
}

.who__traits p {
  margin: 0;
  color: var(--foam);
  line-height: 1.5;
}

.who__traits p + p {
  margin-top: 0.85rem;
}

.who__block {
  margin-bottom: 1.35rem;
}

.who__block h3 {
  font-size: 1.15rem;
  margin-bottom: 0.35rem;
  color: var(--amber-bright);
}

.who__block p {
  color: var(--foam-dim);
}

.who__meme {
  margin: 0 0 1.5rem;
  padding: 0;
  border: 0;
  font-family: var(--font-display);
  font-size: 1.2rem;
  line-height: 1.3;
  color: var(--amber-bright);
}

.who__deity {
  margin-top: 1rem;
  color: var(--foam-dim);
  font-size: 0.95rem;
}

.who__meta {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.85rem 1rem;
  margin: 1.75rem 0 0;
  padding-top: 1.5rem;
  border-top: 1px solid var(--line);
}

.who__meta dt {
  font-size: 0.75rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--amber-bright);
  margin-bottom: 0.15rem;
}

.who__meta dd {
  margin: 0;
  font-weight: 600;
}
</style>
