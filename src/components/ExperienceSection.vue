<template>
  <section id="experience" class="experience">
    <div class="section-header">
      <span class="section-bar"></span>
      <h2>EXPERIENCE</h2>
      <span class="section-bar"></span>
    </div>
    <p class="section-sub">MY PROFESSIONAL JOURNEY</p>
    <div class="timeline">
      <div class="timeline-item" v-for="(item, i) in experience" :key="i">
        <div class="timeline-pixel">
          <div class="pixel-block"></div>
        </div>
        <div class="timeline-content">
          <span class="timeline-date">{{ item.date }}</span>
          <h3>{{ item.title }}</h3>
          <span class="timeline-company">&gt; {{ item.company }}</span>
          <p>{{ item.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const experience = [
  {
    date: '2023 // PRESENT',
    title: 'SR. FRONTEND DEV',
    company: 'TECHCORP INC.',
    description: 'LEADING FRONTEND ARCHITECTURE FOR A SAAS PLATFORM SERVING 50K+ USERS. MIGRATED LEGACY CODEBASE TO VUE 3 + TYPESCRIPT.'
  },
  {
    date: '2021 // 2023',
    title: 'FRONTEND DEVELOPER',
    company: 'STARTUPXYZ',
    description: 'BUILT AND MAINTAINED CLIENT APPLICATIONS USING REACT AND NUXT. INTRODUCED COMPONENT LIBRARY AND DESIGN SYSTEM.'
  },
  {
    date: '2020 // 2021',
    title: 'JUNIOR DEVELOPER',
    company: 'WEBAGENCY',
    description: 'DEVELOPED RESPONSIVE WEBSITES FOR DIVERSE CLIENTS. COLLABORATED WITH DESIGNERS ON PIXEL-PERFECT UI COMPONENTS.'
  }
]
</script>

<style scoped>
.experience {
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
  margin-bottom: 0.5rem;
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
}

.section-sub {
  color: rgba(200, 200, 212, 0.3);
  margin-bottom: 3rem;
  font-size: 0.55rem;
  letter-spacing: 3px;
}

.timeline {
  max-width: 560px;
  width: 100%;
  text-align: left;
  position: relative;
  padding-left: 2.5rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 9px;
  top: 8px;
  bottom: 8px;
  width: 3px;
  background: repeating-linear-gradient(
    to bottom,
    #ffcc00 0px,
    #ffcc00 6px,
    transparent 6px,
    transparent 12px
  );
}

.timeline-item {
  position: relative;
  margin-bottom: 3rem;
}

.timeline-pixel {
  position: absolute;
  left: -2.5rem;
  top: 4px;
}

.pixel-block {
  width: 20px;
  height: 20px;
  background: #ffcc00;
  box-shadow: 5px 5px 0 0 #b38a00;
}

.timeline-date {
  font-size: 0.5rem;
  color: rgba(255, 204, 0, 0.4);
  letter-spacing: 2px;
}

.timeline-content h3 {
  font-size: 0.7rem;
  margin: 0.4rem 0 0.15rem;
  color: #fff;
  letter-spacing: 2px;
}

.timeline-company {
  font-size: 0.55rem;
  color: rgba(255, 204, 0, 0.4);
  letter-spacing: 2px;
}

.timeline-content p {
  font-size: 0.5rem;
  color: rgba(200, 200, 212, 0.4);
  line-height: 2;
  margin-top: 0.5rem;
  letter-spacing: 1px;
}

@media (max-width: 768px) {
  .experience { padding: 5rem 1.5rem 7rem; }
  h2 { font-size: 1.2rem; }
  .section-bar { width: 24px; }
  .section-sub { font-size: 0.45rem; }
  .timeline { padding-left: 2rem; }
  .timeline-pixel { left: -2rem; }
  .pixel-block { width: 16px; height: 16px; box-shadow: 4px 4px 0 0 #b38a00; }
  .timeline::before { left: 7px; }
  .timeline-content p { font-size: 0.4rem; }
}

@media (max-width: 480px) {
  .experience { padding: 4rem 1rem 6rem; }
  .section-header { gap: 0.6rem; }
  h2 { font-size: 0.9rem; letter-spacing: 2px; }
  .section-bar { width: 16px; height: 3px; }
  .section-sub { font-size: 0.38rem; margin-bottom: 2rem; }
  .timeline { padding-left: 1.5rem; }
  .timeline-pixel { left: -1.5rem; }
  .pixel-block { width: 12px; height: 12px; box-shadow: 3px 3px 0 0 #b38a00; }
  .timeline::before { left: 5px; width: 2px; }
  .timeline-item { margin-bottom: 2rem; }
  .timeline-date { font-size: 0.38rem; }
  .timeline-content h3 { font-size: 0.5rem; }
  .timeline-company { font-size: 0.4rem; }
  .timeline-content p { font-size: 0.35rem; }
}

@media (max-width: 360px) {
  .experience { padding: 3rem 0.6rem 5rem; }
  .section-header { gap: 0.4rem; }
  h2 { font-size: 0.65rem; }
  .section-bar { width: 12px; height: 2px; }
  .section-sub { font-size: 0.28rem; }
  .timeline-content h3 { font-size: 0.4rem; }
  .timeline-content p { font-size: 0.28rem; }
}
</style>
