<script setup>
import { ref, onMounted, onUnmounted, watch } from 'vue'
import { useTheme } from '../composables/useTheme'

const { currentTheme, themes } = useTheme()
const canvasRef = ref(null)

let animId = null
let particles = []
let mouse = { x: -1000, y: -1000 }
let lineOpacity = 0.15

function getColors() {
  const t = themes[currentTheme.value] || themes.cyber
  return [t.hex.primary, t.hex.secondary, t.hex.tertiary]
}

function readLineOpacity() {
  const val = getComputedStyle(document.documentElement).getPropertyValue('--particle-line-opacity').trim()
  lineOpacity = parseFloat(val) || 0.15
}

onMounted(() => {
  const canvas = canvasRef.value
  const ctx = canvas.getContext('2d')

  readLineOpacity()

  function resize() {
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
  }

  function hexToRgb(hex) {
    const r = parseInt(hex.slice(1, 3), 16)
    const g = parseInt(hex.slice(3, 5), 16)
    const b = parseInt(hex.slice(5, 7), 16)
    return { r, g, b }
  }

  function createParticle() {
    const colors = getColors()
    const color = colors[Math.floor(Math.random() * colors.length)]
    return {
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      vx: (Math.random() - 0.5) * 0.8,
      vy: (Math.random() - 0.5) * 0.8,
      size: Math.random() * 2 + 0.5,
      color: color,
      rgb: hexToRgb(color),
      alpha: Math.random() * 0.5 + 0.2,
    }
  }

  function init() {
    resize()
    particles = Array.from({ length: 120 }, createParticle)
  }

  function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height)

    particles.forEach((p, i) => {
      p.x += p.vx
      p.y += p.vy

      if (p.x < 0 || p.x > canvas.width) p.vx *= -1
      if (p.y < 0 || p.y > canvas.height) p.vy *= -1

      const dx = mouse.x - p.x
      const dy = mouse.y - p.y
      const dist = Math.sqrt(dx * dx + dy * dy)
      if (dist < 150) {
        p.x -= dx * 0.02
        p.y -= dy * 0.02
      }

      ctx.beginPath()
      ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2)
      ctx.fillStyle = `rgba(${p.rgb.r}, ${p.rgb.g}, ${p.rgb.b}, ${p.alpha})`
      ctx.fill()

      for (let j = i + 1; j < particles.length; j++) {
        const p2 = particles[j]
        const d = Math.hypot(p.x - p2.x, p.y - p2.y)
        if (d < 120) {
          ctx.beginPath()
          ctx.moveTo(p.x, p.y)
          ctx.lineTo(p2.x, p2.y)
          ctx.strokeStyle = `rgba(${p.rgb.r}, ${p.rgb.g}, ${p.rgb.b}, ${(1 - d / 120) * lineOpacity})`
          ctx.lineWidth = 0.5
          ctx.stroke()
        }
      }
    })

    animId = requestAnimationFrame(draw)
  }

  function handleMouse(e) {
    mouse.x = e.clientX
    mouse.y = e.clientY
  }

  window.addEventListener('resize', resize)
  window.addEventListener('mousemove', handleMouse)
  init()
  draw()

  onUnmounted(() => {
    cancelAnimationFrame(animId)
    window.removeEventListener('resize', resize)
    window.removeEventListener('mousemove', handleMouse)
  })
})

watch(currentTheme, () => {
  readLineOpacity()
  const colors = getColors()
  particles.forEach(p => {
    const color = colors[Math.floor(Math.random() * colors.length)]
    p.color = color
    p.rgb = hexToRgb(color)
  })
})

function hexToRgb(hex) {
  const r = parseInt(hex.slice(1, 3), 16)
  const g = parseInt(hex.slice(3, 5), 16)
  const b = parseInt(hex.slice(5, 7), 16)
  return { r, g, b }
}
</script>

<template>
  <canvas ref="canvasRef" class="particle-canvas"></canvas>
</template>

<style scoped>
.particle-canvas {
  position: fixed;
  inset: 0;
  z-index: -1;
  pointer-events: none;
}
</style>
