<template>
  <canvas ref="canvasRef"></canvas>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const canvasRef = ref(null)
let ctx = null
let animationId = null
let drops = []
let blocks = []

const isSmall = window.innerWidth < 480

const BLOCK_SIZE = isSmall ? 16 : 24
const DROP_COUNT = isSmall ? 8 : 30
const BLOCK_COUNT = isSmall ? 4 : 12

class Drop {
  constructor(w) {
    this.reset(w)
  }
  reset(w) {
    this.x = Math.floor(Math.random() * (w / BLOCK_SIZE)) * BLOCK_SIZE
    this.y = -BLOCK_SIZE
    this.speed = 1 + Math.random() * (isSmall ? 2 : 3)
    this.length = 2 + Math.floor(Math.random() * (isSmall ? 3 : 6))
    this.opacity = 0.2 + Math.random() * 0.4
  }
  update(h) {
    this.y += this.speed
    const maxY = h + this.length * BLOCK_SIZE
    if (this.y > maxY) {
      this.y = -this.length * BLOCK_SIZE
      this.x = Math.floor(Math.random() * (window.innerWidth / BLOCK_SIZE)) * BLOCK_SIZE
    }
  }
  draw(ctx) {
    ctx.fillStyle = `rgba(72, 219, 251, ${this.opacity})`
    for (let i = 0; i < this.length; i++) {
      const yy = this.y + i * BLOCK_SIZE
      if (yy > 0 && yy < ctx.canvas.height) {
        ctx.fillRect(this.x, yy, BLOCK_SIZE - 2, BLOCK_SIZE - 2)
      }
    }
  }
}

class Block {
  constructor(w, h) {
    this.reset(w, h)
  }
  reset(w, h) {
    this.x = Math.floor(Math.random() * (w / BLOCK_SIZE)) * BLOCK_SIZE
    this.y = Math.floor(Math.random() * (h / BLOCK_SIZE)) * BLOCK_SIZE
    this.size = (Math.floor(Math.random() * 2) + 1) * BLOCK_SIZE
    this.speed = 0.1 + Math.random() * (isSmall ? 0.15 : 0.3)
    this.opacity = isSmall ? 0.02 : (0.015 + Math.random() * 0.025)
    this.dir = Math.random() > 0.5 ? 1 : -1
  }
  update(w, h) {
    this.x += this.speed * this.dir
    if (this.x < 0 || this.x + this.size > w) this.dir *= -1
  }
  draw(ctx) {
    ctx.fillStyle = `rgba(255, 204, 0, ${this.opacity})`
    ctx.fillRect(this.x, this.y, this.size, this.size)
  }
}

function drawGrid(w, h) {
  const alpha = isSmall ? 0.015 : 0.03
  ctx.strokeStyle = `rgba(72, 219, 251, ${alpha})`
  ctx.lineWidth = 1

  for (let x = 0; x < w; x += BLOCK_SIZE) {
    ctx.beginPath()
    ctx.moveTo(x, 0)
    ctx.lineTo(x, h)
    ctx.stroke()
  }
  for (let y = 0; y < h; y += BLOCK_SIZE) {
    ctx.beginPath()
    ctx.moveTo(0, y)
    ctx.lineTo(w, y)
    ctx.stroke()
  }
}

function resize() {
  const canvas = canvasRef.value
  if (!canvas) return
  canvas.width = window.innerWidth
  canvas.height = window.innerHeight
}

function animate() {
  const canvas = canvasRef.value
  if (!canvas) return
  const w = canvas.width
  const h = canvas.height

  ctx.clearRect(0, 0, w, h)
  drawGrid(w, h)

  for (const b of blocks) {
    b.update(w, h)
    b.draw(ctx)
  }

  for (const d of drops) {
    d.update(h)
    d.draw(ctx)
  }

  animationId = requestAnimationFrame(animate)
}

function onResize() {
  resize()
  const w = canvasRef.value.width
  const h = canvasRef.value.height
  while (blocks.length < BLOCK_COUNT) {
    blocks.push(new Block(w, h))
  }
}

onMounted(() => {
  const canvas = canvasRef.value
  if (!canvas) return
  ctx = canvas.getContext('2d')
  resize()

  const w = canvas.width
  const h = canvas.height

  for (let i = 0; i < DROP_COUNT; i++) {
    const d = new Drop(w)
    d.y = Math.random() * h
    drops.push(d)
  }

  for (let i = 0; i < BLOCK_COUNT; i++) {
    blocks.push(new Block(w, h))
  }

  window.addEventListener('resize', onResize)
  animate()
})

onUnmounted(() => {
  if (animationId) cancelAnimationFrame(animationId)
  window.removeEventListener('resize', onResize)
})
</script>

<style scoped>
canvas {
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
  background-color: #1a1a2e;
}
</style>
