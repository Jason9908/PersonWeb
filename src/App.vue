<template>
  <div class="app">
    <Header />
    <main>
      <AboutSection />
      <TimelineSection />
      <AchievementsSection />
      <QualitiesSection />
      <BookmarksSection />
      <SkillsSection />
      <ContactSection />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import AboutSection from './components/AboutSection.vue'
import TimelineSection from './components/TimelineSection.vue'
import AchievementsSection from './components/AchievementsSection.vue'
import QualitiesSection from './components/QualitiesSection.vue'
import BookmarksSection from './components/BookmarksSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'
</script>

<style scoped>
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: linear-gradient(180deg, var(--bg-darker) 0%, var(--bg-dark) 100%);
}

main {
  flex: 1;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  width: 100%;
}

section {
  padding: 80px 0;
  border-bottom: 1px solid rgba(0, 240, 255, 0.1);
}

section:last-child {
  border-bottom: none;
}
</style>
