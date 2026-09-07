<script setup lang="ts">
import AbilitiesGrid from './components/AbilitiesGrid.vue'
import CombatStats from './components/CombatStats.vue'
import HeroSection from './components/HeroSection.vue'
import IdentitySection from './components/IdentitySection.vue'
import InventoryBar from './components/InventoryBar.vue'
import PlayTips from './components/PlayTips.vue'
import SkillsList from './components/SkillsList.vue'
import TurnCheatSheet from './components/TurnCheatSheet.vue'
</script>

<template>
  <main>
    <HeroSection />
    <nav class="site-nav" aria-label="Разделы">
      <a href="#who">Кто он</a>
      <a href="#combat">Бой</a>
      <a href="#stats">Характеристики</a>
      <a href="#skills">Навыки</a>
      <a href="#gear">Вещи</a>
      <a href="#tips">Как играть</a>
      <a href="#turn">Ход</a>
    </nav>
    <IdentitySection />
    <CombatStats />
    <AbilitiesGrid />
    <SkillsList />
    <InventoryBar />
    <PlayTips />
    <TurnCheatSheet />
  </main>

  <footer class="site-footer">
    <p>Бран «Трактирщик» Каплесбор · шпаргалка к сессии в Виндене</p>
  </footer>
</template>

<style scoped>
.site-footer {
  padding: 2rem var(--pad) 3rem;
  text-align: center;
  color: var(--foam-dim);
  font-size: 0.9rem;
  border-top: 1px solid var(--line);
}
</style>
