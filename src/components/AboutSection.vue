<template>
  <section id="about" class="about">
    <div class="section-header">
      <span class="section-bar"></span>
      <h2>ABOUT</h2>
      <span class="section-bar"></span>
    </div>
    <div class="about-content">
      <div class="about-text">
        <p>I'M A FRONTEND DEVELOPER BASED IN BANGKOK WITH OVER <span class="hl">4 YEARS</span> OF EXPERIENCE CRAFTING MODERN WEB APPLICATIONS.</p>
        <p>MY EXPERTISE SPANS <span class="hl">VUE.JS</span>, <span class="hl">REACT</span>, AND <span class="hl">TYPESCRIPT</span> ECOSYSTEMS, WITH A STRONG FOCUS ON PERFORMANCE AND ACCESSIBILITY.</p>
        <p>OUTSIDE OF CODING, I CONTRIBUTE TO OPEN-SOURCE PROJECTS, WRITE TECHNICAL ARTICLES, AND MENTOR ASPIRING DEVELOPERS.</p>
      </div>
      <div class="about-stats">
        <div class="stat" v-for="s in stats" :key="s.label">
          <span class="stat-num">{{ s.num }}</span>
          <span class="stat-label">{{ s.label }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const stats = [
  { num: '4+', label: 'YEARS EXP' },
  { num: '25+', label: 'PROJECTS' },
  { num: '12+', label: 'CLIENTS' },
  { num: '5', label: 'OS CONTRIB' }
]
</script>

<style scoped>
.about {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 6rem 2rem;
  color: #c8c8d4;
  text-align: center;
}

.section-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 3rem;
}

.section-bar {
  display: inline-block;
  width: 32px;
  height: 4px;
  background: #ffcc00;
  flex-shrink: 0;
}

h2 {
  font-size: 1.6rem;
  color: #fff;
  letter-spacing: 4px;
  flex-shrink: 0;
}

.about-content {
  max-width: 680px;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2.5rem;
}

.about-text p {
  font-size: 0.65rem;
  line-height: 2.2;
  color: rgba(200, 200, 212, 0.65);
  margin-bottom: 1rem;
  letter-spacing: 1.5px;
}

.hl {
  color: #ffcc00;
}

.about-stats {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}

.stat {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  border: 3px solid #16213e;
  min-width: 120px;
  flex: 1;
}

.stat-num {
  font-size: 1.4rem;
  color: #ffcc00;
  margin-bottom: 0.4rem;
}

.stat-label {
  font-size: 0.55rem;
  color: rgba(200, 200, 212, 0.35);
  letter-spacing: 1.5px;
}

@media (max-width: 768px) {
  .about { padding: 5rem 1.5rem 7rem; }
  h2 { font-size: 1.2rem; }
  .section-bar { width: 24px; }
  .about-text p { font-size: 0.5rem; }
  .stat { min-width: 90px; padding: 0.8rem; }
  .stat-num { font-size: 1rem; }
  .stat-label { font-size: 0.4rem; }
}

@media (max-width: 480px) {
  .about { padding: 4rem 1rem 6rem; }
  .section-header { gap: 0.6rem; margin-bottom: 2rem; }
  h2 { font-size: 0.9rem; letter-spacing: 2px; }
  .section-bar { width: 16px; height: 3px; }
  .about-content { gap: 1.5rem; }
  .about-text p { font-size: 0.38rem; letter-spacing: 1px; }
  .stat { min-width: 70px; padding: 0.6rem; border-width: 2px; }
  .stat-num { font-size: 0.8rem; }
  .stat-label { font-size: 0.3rem; }
}

@media (max-width: 360px) {
  .about { padding: 3rem 0.6rem 5rem; }
  .section-header { gap: 0.4rem; margin-bottom: 1.5rem; }
  h2 { font-size: 0.65rem; }
  .section-bar { width: 12px; height: 2px; }
  .about-text p { font-size: 0.28rem; line-height: 2; }
  .stat { min-width: 60px; padding: 0.4rem; }
  .stat-num { font-size: 0.6rem; }
  .stat-label { font-size: 0.25rem; }
}
</style>
