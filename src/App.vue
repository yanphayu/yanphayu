<script setup>
import GridBackground from './components/GridBackground.vue'
import SidebarNav from './components/SidebarNav.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'
</script>

<template>
  <GridBackground />
  <SidebarNav />
  <div class="main">
    <HeroSection />
    <AboutSection />
    <ProjectsSection />
    <ExperienceSection />
    <SkillsSection />
    <ContactSection />
    <AppFooter />
  </div>
</template>

<style>
.main {
  margin-left: 72px;
}

@media (max-width: 768px) {
  .main {
    margin-left: 0;
    padding-bottom: 56px;
  }
}

@media (max-width: 360px) {
  .main {
    padding-bottom: 48px;
  }
}
</style>
