<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeSection = ref('hero')

const navItems = [
  { id: 'hero', label: 'Home', icon: 'home' },
  { id: 'about', label: 'About', icon: 'user' },
  { id: 'projects', label: 'Work', icon: 'code' },
  { id: 'skills', label: 'Skills', icon: 'terminal' },
  { id: 'contact', label: 'Contact', icon: 'mail' },
]

function handleScroll() {
  const sections = navItems.map(item => document.getElementById(item.id))
  const scrollPos = window.scrollY + window.innerHeight / 3

  for (let i = sections.length - 1; i >= 0; i--) {
    if (sections[i] && sections[i].offsetTop <= scrollPos) {
      activeSection.value = navItems[i].id
      break
    }
  }
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<template>
  <nav class="dock">
    <div class="dock-inner">
      <a
        v-for="item in navItems"
        :key="item.id"
        :href="`#${item.id}`"
        class="dock-item"
        :class="{ active: activeSection === item.id }"
      >
        <div class="dock-icon-wrap">
          <svg v-if="item.icon === 'home'" class="dock-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/>
            <polyline points="9 22 9 12 15 12 15 22"/>
          </svg>
          <svg v-else-if="item.icon === 'user'" class="dock-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"/>
            <circle cx="12" cy="7" r="4"/>
          </svg>
          <svg v-else-if="item.icon === 'code'" class="dock-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <polyline points="16 18 22 12 16 6"/>
            <polyline points="8 6 2 12 8 18"/>
          </svg>
          <svg v-else-if="item.icon === 'terminal'" class="dock-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <polyline points="4 17 10 11 4 5"/>
            <line x1="12" y1="19" x2="20" y2="19"/>
          </svg>
          <svg v-else-if="item.icon === 'mail'" class="dock-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
            <polyline points="22,6 12,13 2,6"/>
          </svg>
        </div>
        <span class="dock-label">{{ item.label }}</span>
        <div v-if="activeSection === item.id" class="dock-active-dot"></div>
      </a>
    </div>
  </nav>
</template>
