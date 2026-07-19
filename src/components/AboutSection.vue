<template>
  <section id="about" class="section about">
    <div class="container">
      <h2 class="section-title">About Me</h2>
      <div class="about-content">
        <p class="about-text">
          I'm the one who <span class="about-accent">flies</span> without any components.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-text {
  font-family: 'Space Mono', monospace;
  font-size: 0.9rem;
  line-height: 2;
  color: var(--text-muted);
  max-width: 550px;
  margin: 0 auto;
  text-align: center;
  border-left: 2px solid var(--accent);
  padding-left: 1.5rem;
}

.about-accent {
  color: var(--accent);
  font-weight: 700;
}
</style>
