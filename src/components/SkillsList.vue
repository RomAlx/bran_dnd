<script setup lang="ts">
import { bran, fmtMod } from '../data/bran'
</script>

<template>
  <section id="skills" class="section skills">
    <div class="section__inner">
      <p class="section__eyebrow">Проверки</p>
      <h2 class="section__title">Навыки и спасброски</h2>
      <p class="section__lead">
        Компетентность удваивает бонус мастерства у Обмана и Скрытности — фирменные
        «слово у стойки» и «слинять, когда прижмёт».
      </p>

      <ul class="skill-list">
        <li v-for="skill in bran.skills" :key="skill.name" class="skill">
          <span class="skill__name">{{ skill.name }}</span>
          <span class="skill__bonus">{{ fmtMod(skill.bonus) }}</span>
          <span v-if="skill.note" class="skill__note">{{ skill.note }}</span>
        </li>
      </ul>

      <h3 class="subhead">Спасброски</h3>
      <ul class="save-list">
        <li
          v-for="save in bran.saves"
          :key="save.name"
          class="save"
          :class="{ 'save--pro': save.proficient }"
        >
          <span>{{ save.name }}</span>
          <strong>{{ fmtMod(save.bonus) }}</strong>
        </li>
      </ul>

      <h3 class="subhead">Если навыка нет</h3>
      <p class="langs">
        Всё равно можно пробовать — только модификатор характеристики, без +2 мастерства.
        Каменное знание: История про камень считается как владение ×2, то есть +4.
      </p>
      <ul class="other">
        <li v-for="skill in bran.otherSkills" :key="skill.name">
          <span>{{ skill.name }}</span>
          <span>{{ skill.ability }} {{ fmtMod(skill.bonus) }}</span>
        </li>
      </ul>

      <h3 class="subhead">Языки</h3>
      <ul class="langs-list">
        <li v-for="lang in bran.languages" :key="lang.name">
          <strong>{{ lang.name }}</strong>
          <span>{{ lang.note }}</span>
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.skill-list,
.save-list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.skill {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 0.15rem 0.75rem;
  padding: 0.7rem 0;
  border-bottom: 1px solid var(--line);
}

.skill__name {
  font-weight: 700;
}

.skill__bonus {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--amber-bright);
}

.skill__note {
  grid-column: 1 / -1;
  font-size: 0.85rem;
  color: var(--foam-dim);
}

.subhead {
  margin: 1.75rem 0 0.75rem;
  font-size: 1.15rem;
  color: var(--amber-bright);
}

.save-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.5rem;
}

.save {
  display: flex;
  justify-content: space-between;
  gap: 0.5rem;
  padding: 0.55rem 0.65rem;
  background: rgba(61, 74, 50, 0.22);
  font-size: 0.92rem;
}

.save--pro {
  background: rgba(196, 122, 44, 0.18);
  outline: 1px solid var(--line);
}

.save strong {
  font-family: var(--font-display);
  color: var(--amber-bright);
}

.langs {
  margin: 0 0 0.75rem;
  color: var(--foam-dim);
  font-size: 0.95rem;
}

.other,
.langs-list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.other li,
.langs-list li {
  display: flex;
  justify-content: space-between;
  gap: 0.75rem;
  padding: 0.45rem 0;
  border-bottom: 1px solid rgba(196, 122, 44, 0.18);
  font-size: 0.92rem;
}

.other li span:last-child,
.langs-list span {
  color: var(--foam-dim);
}
</style>
