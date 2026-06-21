<template>
  <aside class="sidebar">
    <div class="sidebar-logo">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
        <rect x="2" y="2" width="20" height="20" fill="#ffcc00"/>
        <rect x="6" y="6" width="4" height="4" fill="#1a1a2e"/>
        <rect x="14" y="6" width="4" height="4" fill="#1a1a2e"/>
        <rect x="6" y="14" width="4" height="4" fill="#1a1a2e"/>
        <rect x="14" y="14" width="4" height="4" fill="#1a1a2e"/>
      </svg>
    </div>
    <nav class="sidebar-nav">
      <a
        v-for="item in navItems"
        :key="item.id"
        :href="'#' + item.id"
        :title="item.label"
        @click.prevent="scrollTo(item.id)"
      >
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" v-html="item.icon"></svg>
      </a>
    </nav>
  </aside>
</template>

<script setup>
const navItems = [
  { id: 'hero', label: 'Home', icon: '<path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/>' },
  { id: 'about', label: 'About', icon: '<path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/>' },
  { id: 'projects', label: 'Projects', icon: '<rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/>' },
  { id: 'experience', label: 'Experience', icon: '<path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/>' },
  { id: 'skills', label: 'Skills', icon: '<circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06A1.65 1.65 0 0 0 4.68 15a1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06A1.65 1.65 0 0 0 9 4.68a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"/>' },
  { id: 'contact', label: 'Contact', icon: '<path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/>' }
]

function scrollTo(id) {
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}
</script>

<style scoped>
.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  width: 72px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.2rem;
  padding: 1.2rem 0;
  z-index: 100;
  border-right: 3px solid #16213e;
  background: #1a1a2e;
}

.sidebar-logo {
  padding-bottom: 0.8rem;
  border-bottom: 2px solid #16213e;
}

.sidebar-nav {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}

.sidebar-nav a {
  color: #4a4a6a;
  transition: all 0.15s;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border: 2px solid transparent;
}

.sidebar-nav a:hover {
  color: #ffcc00;
  border-color: #ffcc00;
  background: rgba(255, 204, 0, 0.05);
}

@media (max-width: 768px) {
  .sidebar {
    top: auto;
    bottom: 0;
    left: 0;
    right: 0;
    width: 100%;
    height: 56px;
    flex-direction: row;
    justify-content: center;
    gap: 0;
    padding: 0;
    border-right: none;
    border-top: 3px solid #16213e;
  }

  .sidebar-logo {
    display: none;
  }

  .sidebar-nav {
    flex-direction: row;
    gap: 0;
    width: 100%;
    justify-content: space-around;
    max-width: 500px;
  }

  .sidebar-nav a {
    width: auto;
    height: 56px;
    padding: 0 0.6rem;
    border: none;
    border-top: 3px solid transparent;
    border-bottom: 3px solid transparent;
  }

  .sidebar-nav a:hover {
    border-color: #ffcc00;
    background: none;
  }
}

@media (max-width: 360px) {
  .sidebar {
    height: 48px;
  }

  .sidebar-nav a {
    height: 48px;
    padding: 0 0.3rem;
  }

  .sidebar-nav a svg {
    width: 16px;
    height: 16px;
  }
}
</style>
