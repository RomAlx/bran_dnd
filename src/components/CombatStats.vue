<script setup lang="ts">
import { bran, fmtMod, guide } from '../data/bran'
</script>

<template>
  <section id="combat" class="section combat">
    <div class="section__inner">
      <p class="section__eyebrow">В бою</p>
      <h2 class="section__title">Боевые числа</h2>
      <p class="section__lead">
        Средний плут-лицо на 1 уровне: не танк и не дырка. Кинжал бьёт с Ловкости.
      </p>

      <div class="combat__grid" role="list">
        <div class="stat" role="listitem">
          <span class="stat__label">Хиты</span>
          <span class="stat__value">{{ bran.combat.hp }}</span>
          <span class="stat__note">{{ bran.combat.hitDie }} + ТЕЛ</span>
        </div>
        <div class="stat" role="listitem">
          <span class="stat__label">КЗ</span>
          <span class="stat__value">{{ bran.combat.ac }}</span>
          <span class="stat__note">{{ bran.combat.acNote }}</span>
        </div>
        <div class="stat" role="listitem">
          <span class="stat__label">Инициатива</span>
          <span class="stat__value">{{ fmtMod(bran.combat.initiative) }}</span>
          <span class="stat__note">мод. Ловкости</span>
        </div>
        <div class="stat" role="listitem">
          <span class="stat__label">Скорость</span>
          <span class="stat__value">{{ bran.combat.speed }}</span>
          <span class="stat__note">футов</span>
        </div>
        <div class="stat" role="listitem">
          <span class="stat__label">БМ</span>
          <span class="stat__value">{{ fmtMod(bran.combat.proficiency) }}</span>
          <span class="stat__note">бонус мастерства</span>
        </div>
        <div class="stat" role="listitem">
          <span class="stat__label">Пасс. воспр.</span>
          <span class="stat__value">{{ bran.combat.passivePerception }}</span>
          <span class="stat__note">навыка нет</span>
        </div>
      </div>

      <div class="weapon">
        <h3>{{ bran.weapon.name }}</h3>
        <p class="weapon__line">
          Атака <strong>{{ fmtMod(bran.weapon.attack) }}</strong>
          · урон <strong>{{ bran.weapon.damage }}</strong> {{ bran.weapon.type }}
        </p>
        <p class="weapon__sneak">
          Формула атаки: {{ bran.weapon.attackFormula }}. Скрытая атака
          <strong>+{{ bran.weapon.sneak }}</strong> только если все пункты ниже верны.
        </p>
        <ul class="checks">
          <li v-for="item in guide.sneak" :key="item">{{ item }}</li>
        </ul>
        <p class="weapon__note">{{ bran.combat.acNote }} Досягаемость кинжала — {{ bran.combat.reach }} фт.</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.combat__grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 0.75rem;
}

.stat {
  padding: 0.9rem 0.85rem;
  background: rgba(61, 74, 50, 0.28);
  border-bottom: 2px solid var(--line);
  transition: background 0.2s ease, border-color 0.2s ease;
}

.stat:active,
.stat:hover {
  background: rgba(196, 122, 44, 0.16);
  border-color: var(--amber);
}

.stat__label {
  display: block;
  font-size: 0.72rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--amber-bright);
  margin-bottom: 0.25rem;
}

.stat__value {
  display: block;
  font-family: var(--font-display);
  font-size: 1.85rem;
  font-weight: 700;
  line-height: 1;
}

.stat__note {
  display: block;
  margin-top: 0.35rem;
  font-size: 0.8rem;
  color: var(--foam-dim);
}

.weapon {
  margin-top: 1.5rem;
  padding-top: 1.25rem;
  border-top: 1px solid var(--line);
}

.weapon h3 {
  font-size: 1.25rem;
  margin-bottom: 0.4rem;
  color: var(--amber-bright);
}

.weapon__line {
  margin-bottom: 0.5rem;
}

.weapon__sneak,
.weapon__note {
  color: var(--foam-dim);
  font-size: 0.95rem;
}

.checks {
  margin: 0.75rem 0;
  padding: 0 0 0 1.1rem;
  color: var(--foam);
}

.checks li + li {
  margin-top: 0.35rem;
}

@media (min-width: 640px) {
  .combat__grid {
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }
}
</style>
