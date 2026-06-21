<template>
  <section id="skills" class="skills">
    <div class="section-header">
      <span class="section-bar"></span>
      <h2>SKILLS</h2>
      <span class="section-bar"></span>
    </div>
    <p class="section-sub">TECHNOLOGIES I WORK WITH DAILY</p>
    <div class="skills-grid">
      <div class="skill-group" v-for="group in skillGroups" :key="group.title">
        <h4>&gt; {{ group.title }}</h4>
        <div class="skill-items">
          <div
            class="skill-item"
            v-for="skill in group.items"
            :key="skill.label"
          >
            <svg width="32" height="32" viewBox="0 0 32 32" fill="none" v-html="skill.icon"></svg>
            <span class="skill-label">{{ skill.label }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skillGroups = [
  {
    title: 'FRONTEND',
    items: [
      { label: 'HTML5', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ffcc00" stroke-width="2.5"/><path d="M9 9h14M9 15h14M9 21h10" stroke="#ffcc00" stroke-width="2.5" stroke-linecap="square"/>' },
      { label: 'CSS3', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#48dbfb" stroke-width="2.5"/><path d="M9 9h14L20 26l-6-2-6 2L9 9z" fill="none" stroke="#48dbfb" stroke-width="2.5" stroke-linecap="square"/>' },
      { label: 'BOOTSTRAP', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ff6b6b" stroke-width="2.5"/><text x="16" y="23" text-anchor="middle" fill="#ff6b6b" font-size="12" font-weight="bold" font-family="system-ui">B</text>' },
      { label: 'TAILWIND', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#48dbfb" stroke-width="2.5"/><path d="M10 16l6-8 6 8-6 8-6-8z" fill="rgba(72,219,251,0.1)" stroke="#48dbfb" stroke-width="2"/>' },
      { label: 'JS', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ffcc00" stroke-width="2.5"/><text x="16" y="23" text-anchor="middle" fill="#ffcc00" font-size="13" font-weight="bold" font-family="system-ui">JS</text>' },
      { label: 'TS', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ff6b6b" stroke-width="2.5"/><text x="16" y="23" text-anchor="middle" fill="#ff6b6b" font-size="12" font-weight="bold" font-family="system-ui">TS</text>' },
      { label: 'REACT', icon: '<circle cx="16" cy="16" r="4" stroke="#ff6b6b" stroke-width="2.5"/><ellipse cx="16" cy="16" rx="10" ry="4" stroke="#ff6b6b" stroke-width="1.5" transform="rotate(0 16 16)"/><ellipse cx="16" cy="16" rx="10" ry="4" stroke="#ff6b6b" stroke-width="1.5" transform="rotate(60 16 16)"/><ellipse cx="16" cy="16" rx="10" ry="4" stroke="#ff6b6b" stroke-width="1.5" transform="rotate(120 16 16)"/>' },
      { label: 'VUE', icon: '<path d="M16 5L5 27h22L16 5z" fill="none" stroke="#48dbfb" stroke-width="2.5" stroke-linejoin="miter"/><path d="M16 5l-5 12 5 7 5-7-5-12z" fill="rgba(72,219,251,0.15)"/>' },
      { label: 'JQUERY', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ffcc00" stroke-width="2.5"/><text x="16" y="23" text-anchor="middle" fill="#ffcc00" font-size="10" font-weight="bold" font-family="system-ui">JQ</text>' }
    ]
  },
  {
    title: 'BACKEND',
    items: [
      { label: 'PHP', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#48dbfb" stroke-width="2.5"/><path d="M6 24V8h6c3 0 5 2 5 5s-2 5-5 5H8" stroke="#48dbfb" stroke-width="2.5" stroke-linecap="square"/><circle cx="6" cy="24" r="1" fill="#48dbfb"/>' },
      { label: 'LARAVEL', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ff6b6b" stroke-width="2.5"/><path d="M8 24V8l10 16V8" stroke="#ff6b6b" stroke-width="2.5" stroke-linecap="square" stroke-linejoin="miter"/>' },
      { label: 'JAVA', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ffcc00" stroke-width="2.5"/><path d="M10 6c-2 4-2 16 0 20" stroke="#ffcc00" stroke-width="2.5" stroke-linecap="square"/><path d="M22 6c2 4 2 16 0 20" stroke="#ff6b6b" stroke-width="2.5" stroke-linecap="square"/><path d="M8 14h16" stroke="#ffcc00" stroke-width="2.5" stroke-linecap="square"/>' },
      { label: 'SPRING', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#48dbfb" stroke-width="2.5"/><path d="M16 6c-6 0-10 4-10 10s4 10 10 10" stroke="#48dbfb" stroke-width="2.5" stroke-linecap="square"/><path d="M16 10c-3 0-6 3-6 6s3 6 6 6" stroke="#ff6b6b" stroke-width="2" stroke-linecap="square"/><path d="M16 14c-1 0-2 1-2 2s1 2 2 2" fill="#48dbfb"/>' }
    ]
  },
  {
    title: 'DATABASE',
    items: [
      { label: 'MYSQL', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#48dbfb" stroke-width="2.5"/><path d="M8 8h16M8 16h16M8 24h10" stroke="#48dbfb" stroke-width="2.5" stroke-linecap="square"/><circle cx="8" cy="24" r="1.5" fill="#48dbfb"/>' },
      { label: 'XAMPP', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ff6b6b" stroke-width="2.5"/><path d="M6 6l20 20M26 6L6 26" stroke="#ff6b6b" stroke-width="2.5" stroke-linecap="square"/>' },
      { label: 'LARAGON', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ffcc00" stroke-width="2.5"/><path d="M10 24V8h12" stroke="#ffcc00" stroke-width="2.5" stroke-linecap="square"/>' }
    ]
  },
  {
    title: 'TOOLS',
    items: [
      { label: 'GIT', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ffcc00" stroke-width="2.5"/><path d="M16 5v10l4 4-4 4" stroke="#ffcc00" stroke-width="2.5" stroke-linecap="square"/><circle cx="11" cy="22" r="2.5" fill="none" stroke="#ffcc00" stroke-width="2.5"/><circle cx="21" cy="18" r="2.5" fill="none" stroke="#ffcc00" stroke-width="2.5"/>' },
      { label: 'VERCEL', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#ffcc00" stroke-width="2.5"/><path d="M16 7l10 20H6l10-20z" fill="none" stroke="#ffcc00" stroke-width="2.5" stroke-linejoin="miter"/>' },
      { label: 'DOCKER', icon: '<rect x="3" y="3" width="26" height="26" fill="none" stroke="#48dbfb" stroke-width="2.5"/><rect x="5" y="13" width="6" height="6" fill="rgba(72,219,251,0.15)"/><rect x="12" y="13" width="6" height="6" fill="rgba(72,219,251,0.15)"/><rect x="19" y="13" width="6" height="6" fill="rgba(72,219,251,0.15)"/><rect x="12" y="20" width="6" height="6" fill="rgba(72,219,251,0.15)"/>' }
    ]
  }
]
</script>

<style scoped>
.skills {
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

.skills-grid {
  display: flex;
  gap: 2.5rem;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 900px;
  width: 100%;
}

.skill-group {
  min-width: 220px;
  flex: 1;
}

.skill-group h4 {
  font-size: 0.55rem;
  color: rgba(255, 204, 0, 0.4);
  text-align: left;
  margin-bottom: 1rem;
  letter-spacing: 3px;
}

.skill-items {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  justify-content: center;
}

.skill-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.6rem 0.8rem;
  border: 3px solid #16213e;
  transition: all 0.15s;
  min-width: 68px;
}

.skill-item:hover {
  border-color: #ffcc00;
  background: rgba(255, 204, 0, 0.03);
}

.skill-label {
  font-size: 0.5rem;
  color: rgba(200, 200, 212, 0.35);
  letter-spacing: 1.5px;
}

@media (max-width: 768px) {
  .skills { padding: 5rem 1.5rem 7rem; }
  h2 { font-size: 1.2rem; }
  .section-bar { width: 24px; }
  .section-sub { font-size: 0.45rem; }
  .skills-grid { gap: 1.5rem; }
  .skill-group { min-width: 160px; }
  .skill-group h4 { font-size: 0.45rem; }
  .skill-item { padding: 0.5rem 0.6rem; border-width: 2px; }
  .skill-item svg { width: 24px; height: 24px; }
  .skill-label { font-size: 0.38rem; }
}

@media (max-width: 480px) {
  .skills { padding: 4rem 1rem 6rem; }
  .section-header { gap: 0.6rem; }
  h2 { font-size: 0.9rem; letter-spacing: 2px; }
  .section-bar { width: 16px; height: 3px; }
  .section-sub { font-size: 0.38rem; margin-bottom: 2rem; }
  .skills-grid { gap: 1rem; }
  .skill-group { min-width: 100%; }
  .skill-group h4 { font-size: 0.38rem; margin-bottom: 0.6rem; }
  .skill-items { gap: 0.4rem; }
  .skill-item { padding: 0.4rem 0.5rem; min-width: 52px; }
  .skill-item svg { width: 20px; height: 20px; }
  .skill-label { font-size: 0.3rem; }
}

@media (max-width: 360px) {
  .skills { padding: 3rem 0.6rem 5rem; }
  .section-header { gap: 0.4rem; }
  h2 { font-size: 0.65rem; }
  .section-bar { width: 12px; height: 2px; }
  .section-sub { font-size: 0.28rem; }
  .skill-item { padding: 0.3rem 0.4rem; min-width: 44px; }
  .skill-item svg { width: 16px; height: 16px; }
  .skill-label { font-size: 0.25rem; }
}
</style>
