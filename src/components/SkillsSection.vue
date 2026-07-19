<script setup>
const skillCategories = [
  {
    title: 'Languages',
    skills: [
      { name: 'JavaScript', icon: 'js' },
      { name: 'TypeScript', icon: 'ts' },
      { name: 'PHP', icon: 'php' },
      { name: 'C++', icon: 'cpp' },
      { name: 'SQL', icon: 'sql' },
    ],
  },
  {
    title: 'Frontend',
    skills: [
      { name: 'React', icon: 'react' },
      { name: 'Vue.js', icon: 'vue' },
      { name: 'HTML5 / CSS3', icon: 'html' },
      { name: 'Tailwind CSS', icon: 'tailwind' },
      { name: 'Bootstrap', icon: 'bootstrap' },
    ],
  },
  {
    title: 'Backend',
    skills: [
      { name: 'Laravel', icon: 'laravel' },
      { name: 'Node.js', icon: 'node' },
      { name: 'REST APIs', icon: 'api' },
    ],
  },
  {
    title: 'Tools',
    skills: [
      { name: 'Git', icon: 'git' },
      { name: 'GitHub', icon: 'github' },
      { name: 'VS Code', icon: 'vscode' },
    ],
  },
]
</script>

<template>
  <section id="skills" class="section skills">
    <div class="container">
      <h2 class="section-title">Skills</h2>
      <div class="skills-grid">
        <div v-for="category in skillCategories" :key="category.title" class="skill-category">
          <h3>{{ category.title }}</h3>
          <ul>
            <li v-for="skill in category.skills" :key="skill.name">
              <svg v-if="skill.icon === 'js'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#F7DF1E"/><text x="12" y="18" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="12" fill="#000">JS</text></svg>
              <svg v-else-if="skill.icon === 'ts'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#3178C6"/><text x="12" y="18" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="12" fill="#fff">TS</text></svg>
              <svg v-else-if="skill.icon === 'php'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#777BB4"/><text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="11" fill="#fff">PHP</text></svg>
              <svg v-else-if="skill.icon === 'cpp'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#00599C"/><text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="9" fill="#fff">C++</text></svg>
              <svg v-else-if="skill.icon === 'sql'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#4479A1"/><text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="9" fill="#fff">SQL</text></svg>
              <svg v-else-if="skill.icon === 'react'" class="skill-icon" viewBox="0 0 24 24"><circle cx="12" cy="12" r="2.5" fill="#61DAFB"/><ellipse cx="12" cy="12" rx="10" ry="4" fill="none" stroke="#61DAFB" stroke-width="1"/><ellipse cx="12" cy="12" rx="10" ry="4" fill="none" stroke="#61DAFB" stroke-width="1" transform="rotate(60 12 12)"/><ellipse cx="12" cy="12" rx="10" ry="4" fill="none" stroke="#61DAFB" stroke-width="1" transform="rotate(-60 12 12)"/></svg>
              <svg v-else-if="skill.icon === 'vue'" class="skill-icon" viewBox="0 0 24 24"><path d="M2 3h3.5L12 14.5 18.5 3H22L12 21 2 3z" fill="#42B883"/><path d="M5.5 3L12 14.5 18.5 3H15L12 8.5 9 3H5.5z" fill="#35495E"/></svg>
              <svg v-else-if="skill.icon === 'html'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#E34F26"/><text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="8" fill="#fff">HTML</text></svg>
              <svg v-else-if="skill.icon === 'tailwind'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#06B6D4"/><text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="10" fill="#fff">TW</text></svg>
              <svg v-else-if="skill.icon === 'bootstrap'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#7952B3"/><text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="10" fill="#fff">BS</text></svg>
              <svg v-else-if="skill.icon === 'laravel'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#FF2D20"/><text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="11" fill="#fff">Lr</text></svg>
              <svg v-else-if="skill.icon === 'node'" class="skill-icon" viewBox="0 0 24 24"><path d="M12 2L2 7v10l10 5 10-5V7L12 2z" fill="#339933"/><text x="12" y="16" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="9" fill="#fff">N</text></svg>
              <svg v-else-if="skill.icon === 'api'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#1e1e2e" stroke="var(--neon-cyan)" stroke-width="1"/><text x="12" y="16" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="8" fill="var(--neon-cyan)">API</text></svg>
              <svg v-else-if="skill.icon === 'git'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#F05032"/><text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="10" fill="#fff">Git</text></svg>
              <svg v-else-if="skill.icon === 'github'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#181717"/><path d="M12 2C6.477 2 2 6.477 2 12c0 4.42 2.87 8.17 6.84 9.5.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34-.46-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.87 1.52 2.34 1.07 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.55-1.11-4.55-4.92 0-1.11.38-2 1.03-2.71-.1-.25-.45-1.29.1-2.64 0 0 .84-.27 2.75 1.02.79-.22 1.65-.33 2.5-.33.85 0 1.71.11 2.5.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.35.2 2.39.1 2.64.65.71 1.03 1.6 1.03 2.71 0 3.82-2.34 4.66-4.57 4.91.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0012 2z" fill="#fff"/></svg>
              <svg v-else-if="skill.icon === 'vscode'" class="skill-icon" viewBox="0 0 24 24"><rect width="24" height="24" rx="2" fill="#007ACC"/><text x="12" y="16" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="7" fill="#fff">VS</text></svg>
              <span>{{ skill.name }}</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skill-icon {
  width: 22px;
  height: 22px;
  flex-shrink: 0;
  margin-right: 0.5rem;
  vertical-align: middle;
}

li {
  display: flex;
  align-items: center;
  padding: 0.35rem 0;
  font-size: 0.82rem;
}
</style>
