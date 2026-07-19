<script setup>
import GlitchText from './GlitchText.vue'
</script>

<template>
  <header id="hero" class="hero">
    <div class="hero-content">
      <div class="hero-avatar-wrapper">
        <div class="avatar-ring ring-1"></div>
        <div class="avatar-ring ring-2"></div>
        <img src="/image.png" alt="Yan Phayu" class="hero-avatar" />
        <div class="avatar-glitch"></div>
      </div>
      <GlitchText tag="h1" :text="'YAN PHAYU'" class="hero-name" />
      <div class="hero-buttons">
        <a href="#projects" class="btn btn-primary">
          <span class="btn-text">View My Work</span>
          <span class="btn-glitch" aria-hidden="true">View My Work</span>
        </a>
        <a href="#contact" class="btn btn-outline">
          <span class="btn-text">Get In Touch</span>
          <span class="btn-glitch" aria-hidden="true">Get In Touch</span>
        </a>
      </div>
    </div>

    <div class="floating-orb orb-1"></div>
    <div class="floating-orb orb-2"></div>
    <div class="floating-orb orb-3"></div>
  </header>
</template>
