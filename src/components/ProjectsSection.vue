<script setup>
const projects = [
  {
    title: 'Project One',
    description: 'A brief description of this project and the technologies used.',
    tags: ['React', 'Node.js'],
    demo: '#',
    github: '#',
  },
  {
    title: 'Project Two',
    description: 'A brief description of this project and the technologies used.',
    tags: ['Vue.js', 'Laravel'],
    demo: '#',
    github: '#',
  },
  {
    title: 'Project Three',
    description: 'A brief description of this project and the technologies used.',
    tags: ['PHP', 'MySQL'],
    demo: '#',
    github: '#',
  },
]
</script>

<template>
  <section id="projects" class="section projects">
    <div class="container">
      <h2 class="section-title">Projects</h2>
      <div class="projects-grid">
        <div v-for="project in projects" :key="project.title" class="project-card">
          <div class="project-image"></div>
          <div class="project-info">
            <h3 class="project-title">{{ project.title }}</h3>
            <p class="project-description">{{ project.description }}</p>
            <div class="project-tags">
              <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
            <div class="project-links">
              <a :href="project.demo" class="btn btn-small">Live Demo</a>
              <a :href="project.github" class="btn btn-small btn-outline">GitHub</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
