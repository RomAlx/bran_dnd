<script setup lang="ts">
import { guide } from '../data/bran'
</script>

<template>
  <section id="turn" class="section turn">
    <div class="section__inner">
      <p class="section__eyebrow">Шпаргалка на ход</p>
      <h2 class="section__title">Что можно сделать</h2>
      <p class="section__lead">
        В свой ход обычно: движение + одно действие. Бонусное у Брана пока пустое.
        Реакция — отдельно, часто не в твой ход.
      </p>

      <article v-for="step in guide.turnOrder" :key="step.title" class="block">
        <h3>{{ step.title }}</h3>
        <p>{{ step.body }}</p>
      </article>

      <h3 class="subhead">Действия — выбери одно</h3>
      <ul class="actions">
        <li v-for="a in guide.actions" :key="a.name">
          <strong>{{ a.name }}</strong>
          <span class="when">{{ a.when }}</span>
          <span>{{ a.tip }}</span>
        </li>
      </ul>

      <h3 class="subhead">Движение</h3>
      <ul class="move">
        <li v-for="m in guide.movement" :key="m.name">
          <span>{{ m.name }}</span>
          <span>{{ m.cost }}</span>
        </li>
      </ul>

      <h3 class="subhead">Если хиты кончились</h3>
      <ul class="zero">
        <li v-for="line in guide.zeroHp" :key="line">{{ line }}</li>
      </ul>

      <h3 class="subhead">Привал</h3>
      <ul class="zero">
        <li v-for="line in guide.rest" :key="line">{{ line }}</li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.block {
  padding: 0.85rem 0;
  border-bottom: 1px solid var(--line);
}

.block h3,
.subhead {
  font-size: 1.15rem;
  color: var(--amber-bright);
  margin-bottom: 0.35rem;
}

.block p {
  color: var(--foam-dim);
}

.subhead {
  margin-top: 1.75rem;
}

.actions,
.move,
.zero {
  list-style: none;
  margin: 0;
  padding: 0;
}

.actions li {
  display: grid;
  gap: 0.2rem;
  padding: 0.8rem 0;
  border-bottom: 1px solid rgba(196, 122, 44, 0.18);
}

.when,
.move span:last-child,
.actions span:last-child,
.zero li {
  color: var(--foam-dim);
}

.move li {
  display: flex;
  justify-content: space-between;
  gap: 0.75rem;
  padding: 0.5rem 0;
  border-bottom: 1px solid rgba(196, 122, 44, 0.18);
}

.zero {
  padding-left: 1.1rem;
  list-style: disc;
}

.zero li + li {
  margin-top: 0.45rem;
}
</style>
