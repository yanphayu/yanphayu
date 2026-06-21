<template>
  <section id="projects" class="projects">
    <div class="section-header">
      <span class="section-bar"></span>
      <h2>PROJECTS</h2>
      <span class="section-bar"></span>
    </div>
    <p class="section-sub">A SELECTION OF PROJECTS I'VE BUILT</p>
    <div class="project-grid">
      <div
        class="project-card"
        v-for="project in projects"
        :key="project.title"
      >
        <div class="card-top" :style="{ background: project.color }">
          <div class="card-pixels">
            <span v-for="p in 18" :key="p" class="pixel-light"></span>
          </div>
          <span class="card-icon">{{ project.emoji }}</span>
        </div>
        <div class="card-body">
          <div class="card-tags">
            <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
          </div>
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    color: '#2a1a3e',
    emoji: '[+]',
    tags: ['VUE3', 'TS', 'TW'],
    title: 'PULSE DASHBOARD',
    description: 'REAL-TIME ANALYTICS DASHBOARD WITH INTERACTIVE CHARTS, DATA EXPORT, AND ROLE-BASED TEAM WORKSPACES.'
  },
  {
    color: '#1a2e2a',
    emoji: '[$]',
    tags: ['REACT', 'NODE', 'STRIPE'],
    title: 'MERIDIAN SHOP',
    description: 'FULL-FEATURED E-COMMERCE PLATFORM WITH SUBSCRIPTION BILLING, MULTI-CURRENCY, AND INVENTORY TRACKING.'
  },
  {
    color: '#2e1a2a',
    emoji: '[@]',
    tags: ['NUXT', 'SUPABASE', 'VRC'],
    title: 'DRIFT SOCIAL',
    description: 'REAL-TIME MESSAGING WITH END-TO-END ENCRYPTION, FILE SHARING, AND VIDEO CALLS.'
  },
  {
    color: '#1a2a2e',
    emoji: '[#]',
    tags: ['NEXT', 'PRISMA', 'PG'],
    title: 'CANVAS LMS',
    description: 'LEARNING MANAGEMENT SYSTEM WITH COURSE CREATION, PROGRESS TRACKING, AND COLLABORATION TOOLS.'
  },
  {
    color: '#2e2a1a',
    emoji: '[&]',
    tags: ['LARAVEL', 'MYSQL', 'DOCKER'],
    title: 'INVENTORY PRO',
    description: 'INVENTORY MANAGEMENT SYSTEM WITH REAL-TIME STOCK TRACKING, SUPPLIER MANAGEMENT, AND AUTO-REORDER NOTIFICATIONS.'
  },
  {
    color: '#1a2e2e',
    emoji: '[%]',
    tags: ['SPRING', 'JAVA', 'VERCEL'],
    title: 'API GATEWAY',
    description: 'MICROSERVICES API GATEWAY WITH RATE LIMITING, AUTHENTICATION, SERVICE DISCOVERY, AND CENTRALIZED LOGGING.'
  }
]
</script>

<style scoped>
.projects {
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

.project-grid {
  display: flex;
  gap: 1.5rem;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 1020px;
  width: 100%;
}

.project-card {
  width: 240px;
  border: 3px solid #16213e;
  text-align: left;
  transition: all 0.15s;
}

.project-card:hover {
  border-color: #ffcc00;
  transform: translate(-3px, -3px);
  box-shadow: 6px 6px 0 0 rgba(255, 204, 0, 0.15);
}

.card-top {
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.card-pixels {
  position: absolute;
  display: flex;
  flex-wrap: wrap;
  gap: 3px;
  padding: 6px;
}

.pixel-light {
  width: 5px;
  height: 5px;
  background: rgba(255, 204, 0, 0.3);
}

.card-icon {
  font-size: 1.6rem;
  color: rgba(255, 204, 0, 0.4);
  position: relative;
  z-index: 1;
}

.card-body {
  padding: 1rem 1rem 1.2rem;
}

.card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  margin-bottom: 0.7rem;
}

.card-tags span {
  font-size: 0.5rem;
  padding: 0.2rem 0.5rem;
  border: 2px solid rgba(255, 204, 0, 0.15);
  color: rgba(255, 204, 0, 0.5);
  letter-spacing: 1.5px;
}

.card-body h3 {
  font-size: 0.7rem;
  margin-bottom: 0.5rem;
  color: #fff;
  letter-spacing: 2px;
}

.card-body p {
  font-size: 0.5rem;
  color: rgba(200, 200, 212, 0.4);
  line-height: 2;
  letter-spacing: 1px;
}

@media (max-width: 768px) {
  .projects { padding: 5rem 1.5rem 7rem; }
  h2 { font-size: 1.2rem; }
  .section-bar { width: 24px; }
  .section-sub { font-size: 0.45rem; }
  .project-card { width: 200px; }
  .card-top { height: 80px; }
  .card-icon { font-size: 1.2rem; }
  .card-body p { font-size: 0.4rem; }
}

@media (max-width: 480px) {
  .projects { padding: 4rem 1rem 6rem; }
  .section-header { gap: 0.6rem; }
  h2 { font-size: 0.9rem; letter-spacing: 2px; }
  .section-bar { width: 16px; height: 3px; }
  .section-sub { font-size: 0.38rem; letter-spacing: 2px; margin-bottom: 2rem; }
  .project-grid { gap: 1rem; }
  .project-card { width: 100%; max-width: 300px; border-width: 2px; }
  .card-top { height: 70px; }
  .card-icon { font-size: 1rem; }
  .card-body h3 { font-size: 0.55rem; }
  .card-body p { font-size: 0.35rem; }
  .card-tags span { font-size: 0.38rem; border-width: 1px; }
}

@media (max-width: 360px) {
  .projects { padding: 3rem 0.6rem 5rem; }
  .section-header { gap: 0.4rem; }
  h2 { font-size: 0.65rem; }
  .section-bar { width: 12px; height: 2px; }
  .section-sub { font-size: 0.28rem; }
  .project-card { max-width: 220px; }
  .card-body { padding: 0.6rem 0.6rem 0.8rem; }
  .card-body h3 { font-size: 0.45rem; }
  .card-body p { font-size: 0.28rem; }
  .card-tags span { font-size: 0.3rem; }
}
</style>
