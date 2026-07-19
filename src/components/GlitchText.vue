<script setup>
defineProps({
  tag: { type: String, default: 'h1' },
  text: { type: String, required: true },
})
</script>

<template>
  <component :is="tag" class="glitch" :data-text="text">
    {{ text }}
  </component>
</template>

<style scoped>
.glitch {
  position: relative;
  display: inline-block;
}

.glitch::before,
.glitch::after {
  content: attr(data-text);
  position: absolute;
  inset: 0;
  overflow: hidden;
}

.glitch::before {
  left: 2px;
  text-shadow: -2px 0 var(--neon-secondary);
  clip-path: inset(0 0 65% 0);
  animation: glitch-top 3s infinite linear alternate-reverse;
}

.glitch::after {
  left: -2px;
  text-shadow: 2px 0 var(--neon-primary);
  clip-path: inset(65% 0 0 0);
  animation: glitch-bottom 2.5s infinite linear alternate-reverse;
}

@keyframes glitch-top {
  0%, 90%, 100% { clip-path: inset(0 0 65% 0); transform: translate(0); }
  92% { clip-path: inset(10% 0 55% 0); transform: translate(-5px, 2px); }
  94% { clip-path: inset(30% 0 40% 0); transform: translate(5px, -1px); }
  96% { clip-path: inset(5% 0 70% 0); transform: translate(-3px, 1px); }
  98% { clip-path: inset(50% 0 20% 0); transform: translate(4px, -2px); }
}

@keyframes glitch-bottom {
  0%, 88%, 100% { clip-path: inset(65% 0 0 0); transform: translate(0); }
  90% { clip-path: inset(55% 0 10% 0); transform: translate(4px, -1px); }
  93% { clip-path: inset(70% 0 5% 0); transform: translate(-4px, 2px); }
  95% { clip-path: inset(60% 0 15% 0); transform: translate(3px, 1px); }
  97% { clip-path: inset(75% 0 0% 0); transform: translate(-5px, -1px); }
}
</style>
