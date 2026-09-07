<script setup lang="ts">
import { bran } from '../data/bran'
</script>

<template>
  <section id="gear" class="section gear">
    <div class="section__inner">
      <p class="section__eyebrow">На поясе</p>
      <h2 class="section__title">Умения и снаряжение</h2>
      <p class="section__lead">Заклинаний нет. Всё через фокусы, кинжал и зелья.</p>

      <div class="features">
        <article v-for="f in bran.features" :key="f.title" class="feature">
          <h3>{{ f.title }}</h3>
          <p>{{ f.body }}</p>
        </article>
      </div>

      <ul class="caveats">
        <li v-for="note in bran.caveats" :key="note">{{ note }}</li>
      </ul>

      <ul class="inv">
        <li v-for="item in bran.inventory" :key="item.name">
          <span>{{ item.name }}</span>
          <span>{{ item.detail }}</span>
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.features {
  display: grid;
  gap: 1rem;
  margin-bottom: 1.75rem;
}

.feature h3 {
  font-size: 1.1rem;
  margin-bottom: 0.3rem;
  color: var(--amber-bright);
}

.feature p {
  color: var(--foam-dim);
  font-size: 0.95rem;
}

.caveats {
  margin: 0 0 1.25rem;
  padding: 0 0 0 1.1rem;
  color: var(--foam-dim);
}

.caveats li + li {
  margin-top: 0.45rem;
}

.inv {
  list-style: none;
  margin: 0;
  padding: 1rem 0 0;
  border-top: 1px solid var(--line);
}

.inv li {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  padding: 0.65rem 0;
  border-bottom: 1px solid rgba(196, 122, 44, 0.18);
  font-weight: 600;
}

.inv li span:last-child {
  color: var(--foam-dim);
  font-weight: 400;
  text-align: right;
}
</style>
