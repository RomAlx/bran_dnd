<script setup lang="ts">
import { guide } from '../data/bran'
</script>

<template>
  <section id="tips" class="section tips">
    <div class="section__inner">
      <p class="section__eyebrow">Первая игра</p>
      <h2 class="section__title">Как это устроено</h2>
      <p class="section__lead">
        Это не квест с кнопками. Мастер ведёт мир, ты ведёшь Брана. Куб — только когда
        исход под вопросом.
      </p>

      <ol class="loop">
        <li v-for="step in guide.loop" :key="step">{{ step }}</li>
      </ol>

      <h3 class="subhead">Как заявлять</h3>
      <ul class="say">
        <li v-for="line in guide.sayIt" :key="line.good">
          <p><span>Не так</span> {{ line.bad }}</p>
          <p><span>Так</span> {{ line.good }}</p>
        </li>
      </ul>

      <h3 class="subhead">Четыре броска, которые встретятся</h3>
      <p class="lead-tight">
        Формула всегда <strong>к20 + модификаторы</strong>. Успех, если итог не меньше
        числа, которое назвал мастер.
      </p>
      <article v-for="roll in guide.rolls" :key="roll.title" class="tip">
        <header>
          <h3>{{ roll.title }}</h3>
          <span>{{ roll.formula }}</span>
        </header>
        <p>{{ roll.body }}</p>
      </article>

      <p class="adv">{{ guide.advantage }}</p>

      <h3 class="subhead">Фразы</h3>
      <ul class="phrases">
        <li v-for="p in guide.phrases" :key="p.label">
          <strong>«{{ p.label }}»</strong>
          <span>{{ p.text }}</span>
        </li>
      </ul>

      <h3 class="subhead">Чтобы не словить взгляд мастера</h3>
      <ul class="dont">
        <li v-for="item in guide.dont" :key="item">{{ item }}</li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.loop {
  margin: 0 0 1.5rem;
  padding-left: 1.2rem;
}

.loop li + li {
  margin-top: 0.45rem;
}

.subhead {
  margin: 1.75rem 0 0.75rem;
  font-size: 1.15rem;
  color: var(--amber-bright);
}

.lead-tight {
  margin-bottom: 1rem;
  color: var(--foam-dim);
}

.say,
.phrases,
.dont {
  list-style: none;
  margin: 0;
  padding: 0;
}

.say li,
.phrases li {
  display: grid;
  gap: 0.35rem;
  padding: 0.75rem 0;
  border-bottom: 1px solid var(--line);
}

.say span {
  display: inline-block;
  min-width: 3.2rem;
  margin-right: 0.4rem;
  font-size: 0.72rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--amber-bright);
}

.tip {
  padding: 0.85rem 0;
  border-bottom: 1px solid var(--line);
}

.tip header {
  display: flex;
  justify-content: space-between;
  gap: 0.75rem;
  align-items: baseline;
  margin-bottom: 0.35rem;
}

.tip h3 {
  font-size: 1.15rem;
}

.tip header span {
  font-family: var(--font-display);
  color: var(--amber-bright);
  font-weight: 700;
  white-space: nowrap;
}

.tip p,
.phrases span,
.dont li {
  color: var(--foam-dim);
}

.adv {
  margin: 1.25rem 0 0;
  padding: 0.9rem 0 0.9rem 1rem;
  border-left: 3px solid var(--amber);
}

.dont {
  display: grid;
  gap: 0.55rem;
  padding-left: 1.1rem;
  list-style: disc;
}

.phrases strong {
  display: block;
}
</style>
