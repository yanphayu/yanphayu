<script setup>
const techs = [
  { name: 'JavaScript', icon: 'js' },
  { name: 'TypeScript', icon: 'ts' },
  { name: 'Vue.js', icon: 'vue' },
  { name: 'React', icon: 'react' },
  { name: 'Laravel', icon: 'laravel' },
  { name: 'Node.js', icon: 'node' },
  { name: 'PHP', icon: 'php' },
  { name: 'Tailwind', icon: 'tailwind' },
  { name: 'Git', icon: 'git' },
  { name: 'C++', icon: 'cpp' },
]
</script>

<template>
  <div class="marquee-wrapper">
    <div class="marquee">
      <div v-for="(tech, i) in [...techs, ...techs]" :key="i" class="marquee-item">
        <svg v-if="tech.icon === 'js'" class="tech-icon" viewBox="0 0 24 24" fill="#F7DF1E">
          <rect width="24" height="24" rx="2" fill="#F7DF1E"/>
          <text x="12" y="18" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="12" fill="#000">JS</text>
        </svg>
        <svg v-else-if="tech.icon === 'ts'" class="tech-icon" viewBox="0 0 24 24">
          <rect width="24" height="24" rx="2" fill="#3178C6"/>
          <text x="12" y="18" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="12" fill="#fff">TS</text>
        </svg>
        <svg v-else-if="tech.icon === 'vue'" class="tech-icon" viewBox="0 0 24 24">
          <path d="M2 3h3.5L12 14.5 18.5 3H22L12 21 2 3z" fill="#42B883"/>
          <path d="M5.5 3L12 14.5 18.5 3H15L12 8.5 9 3H5.5z" fill="#35495E"/>
        </svg>
        <svg v-else-if="tech.icon === 'react'" class="tech-icon" viewBox="0 0 24 24">
          <circle cx="12" cy="12" r="2.5" fill="#61DAFB"/>
          <ellipse cx="12" cy="12" rx="10" ry="4" fill="none" stroke="#61DAFB" stroke-width="1"/>
          <ellipse cx="12" cy="12" rx="10" ry="4" fill="none" stroke="#61DAFB" stroke-width="1" transform="rotate(60 12 12)"/>
          <ellipse cx="12" cy="12" rx="10" ry="4" fill="none" stroke="#61DAFB" stroke-width="1" transform="rotate(-60 12 12)"/>
        </svg>
        <svg v-else-if="tech.icon === 'laravel'" class="tech-icon" viewBox="0 0 24 24">
          <rect width="24" height="24" rx="2" fill="#FF2D20"/>
          <text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="11" fill="#fff">Lr</text>
        </svg>
        <svg v-else-if="tech.icon === 'node'" class="tech-icon" viewBox="0 0 24 24">
          <path d="M12 2L2 7v10l10 5 10-5V7L12 2z" fill="#339933"/>
          <text x="12" y="16" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="9" fill="#fff">N</text>
        </svg>
        <svg v-else-if="tech.icon === 'php'" class="tech-icon" viewBox="0 0 24 24">
          <rect width="24" height="24" rx="2" fill="#777BB4"/>
          <text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="11" fill="#fff">PHP</text>
        </svg>
        <svg v-else-if="tech.icon === 'tailwind'" class="tech-icon" viewBox="0 0 24 24">
          <rect width="24" height="24" rx="2" fill="#06B6D4"/>
          <text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="10" fill="#fff">TW</text>
        </svg>
        <svg v-else-if="tech.icon === 'git'" class="tech-icon" viewBox="0 0 24 24">
          <rect width="24" height="24" rx="2" fill="#F05032"/>
          <text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="11" fill="#fff">Git</text>
        </svg>
        <svg v-else-if="tech.icon === 'cpp'" class="tech-icon" viewBox="0 0 24 24">
          <rect width="24" height="24" rx="2" fill="#00599C"/>
          <text x="12" y="17" text-anchor="middle" font-family="monospace" font-weight="bold" font-size="9" fill="#fff">C++</text>
        </svg>
        <span class="tech-name">{{ tech.name }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.marquee-wrapper {
  overflow: hidden;
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  padding: 1.25rem 0;
  background: rgba(0, 240, 255, 0.02);
  position: relative;
}

.marquee-wrapper::before,
.marquee-wrapper::after {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  width: 120px;
  z-index: 2;
}

.marquee-wrapper::before {
  left: 0;
  background: linear-gradient(90deg, var(--bg), transparent);
}

.marquee-wrapper::after {
  right: 0;
  background: linear-gradient(-90deg, var(--bg), transparent);
}

.marquee {
  display: flex;
  gap: 2.5rem;
  animation: marquee 30s linear infinite;
  white-space: nowrap;
  width: max-content;
}

.marquee-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  flex-shrink: 0;
}

.tech-icon {
  width: 28px;
  height: 28px;
  flex-shrink: 0;
}

.tech-name {
  font-family: 'Space Mono', monospace;
  font-size: 0.7rem;
  text-transform: uppercase;
  letter-spacing: 3px;
  color: var(--border);
  transition: all 0.3s ease;
}

.marquee:hover .tech-name {
  color: var(--neon-cyan);
  text-shadow: var(--glow-cyan);
}

@keyframes marquee {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
</style>
