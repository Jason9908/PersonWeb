<template>
  <div class="app grid-background">
    <Header />
    <main>
      <AboutSection />
      <TimelineSection />
      <CodingJourneySection />
      <QualitiesSection />
      <AchievementsSection />
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
import CodingJourneySection from './components/CodingJourneySection.vue'
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
  position: relative;
}

main {
  flex: 1;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  width: 100%;
  position: relative;
  z-index: 10;
}

section {
  padding: 80px 0;
  position: relative;
}

section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(180deg, transparent 0%, rgba(17, 24, 39, 0.5) 100%);
  pointer-events: none;
}

section:last-child {
  border-bottom: none;
}
</style>
