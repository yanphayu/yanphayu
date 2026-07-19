<script setup>
import { ref } from 'vue'
import { useTheme } from '../composables/useTheme'

const { themes, currentTheme, themeList } = useTheme()
const isOpen = ref(false)

function selectTheme(id) {
  currentTheme.value = id
  isOpen.value = false
}
</script>

<template>
  <div class="theme-switcher" @mouseleave="isOpen = false">
    <button class="theme-toggle" @click="isOpen = !isOpen" title="Change theme">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <circle cx="12" cy="12" r="5"/>
        <line x1="12" y1="1" x2="12" y2="3"/>
        <line x1="12" y1="21" x2="12" y2="23"/>
        <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/>
        <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
        <line x1="1" y1="12" x2="3" y2="12"/>
        <line x1="21" y1="12" x2="23" y2="12"/>
        <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/>
        <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
      </svg>
    </button>
    <Transition name="pop">
      <div v-if="isOpen" class="theme-panel">
        <span class="theme-panel-title">Theme</span>
        <button
          v-for="theme in themeList"
          :key="theme.id"
          class="theme-option"
          :class="{ active: currentTheme === theme.id }"
          @click="selectTheme(theme.id)"
        >
          <span
            class="theme-dot"
            :style="{ background: themes[theme.id].colors['--neon-primary'] }"
          ></span>
          {{ theme.label }}
        </button>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
.theme-switcher {
  position: fixed;
  top: 1.5rem;
  right: 1.5rem;
  z-index: 200;
}

.theme-toggle {
  width: 42px;
  height: 42px;
  border-radius: 12px;
  border: 1px solid var(--border);
  background: var(--bg-card);
  backdrop-filter: blur(16px);
  color: var(--neon-primary);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.25s ease;
}

.theme-toggle:hover {
  border-color: var(--neon-primary);
  box-shadow: var(--glow-primary);
  transform: rotate(30deg);
}

.theme-panel {
  position: absolute;
  top: 50px;
  right: 0;
  background: var(--bg-card);
  backdrop-filter: blur(20px);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 0.75rem;
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  min-width: 140px;
}

.theme-panel-title {
  font-family: 'Space Mono', monospace;
  font-size: 0.55rem;
  text-transform: uppercase;
  letter-spacing: 3px;
  color: var(--text);
  padding: 0.25rem 0.5rem 0.5rem;
}

.theme-option {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.5rem 0.6rem;
  border: none;
  background: transparent;
  color: var(--text);
  font-family: 'Space Mono', monospace;
  font-size: 0.65rem;
  letter-spacing: 1px;
  cursor: pointer;
  border-radius: 8px;
  transition: all 0.2s ease;
}

.theme-option:hover {
  background: var(--border);
  color: var(--text-heading);
}

.theme-option.active {
  background: var(--border);
  color: var(--text-heading);
}

.theme-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  flex-shrink: 0;
  box-shadow: 0 0 8px currentColor;
}

.pop-enter-active {
  transition: all 0.2s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.pop-leave-active {
  transition: all 0.15s ease;
}

.pop-enter-from,
.pop-leave-to {
  opacity: 0;
  transform: translateY(-8px) scale(0.95);
}
</style>
