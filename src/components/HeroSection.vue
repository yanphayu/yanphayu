<template>
  <section id="hero" class="hero">
    <div class="hero-content">
      <div class="pixel-badge">PRESS START</div>
      <div class="pixel-avatar">
        <div v-for="(row, ri) in avatar" :key="ri" class="pixel-row">
          <div
            v-for="(pixel, ci) in row"
            :key="ci"
            class="pixel"
            :class="pixel === '.' ? 'e' : pixel.toLowerCase()"
          ></div>
        </div>
      </div>
      <h1>
        <span class="char" v-for="(c, i) in nameChars" :key="i" :style="{ animationDelay: i * 0.08 + 's' }">{{ c }}</span>
      </h1>
      <p class="subtitle">&gt; {{ displayText }}<span class="cursor">_</span></p>
      <p class="tagline">{{ tagline }}</p>
      <div class="hero-btns">
        <a href="#projects" class="btn btn-pixel" @click.prevent="scrollTo('projects')">
          <span class="btn-text">VIEW PROJECTS</span>
        </a>
        <a href="#contact" class="btn btn-pixel-outline" @click.prevent="scrollTo('contact')">
          <span class="btn-text">CONTACT</span>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const displayText = ref('')
const tagline = 'I BUILD FAST, ACCESSIBLE, AND BEAUTIFUL WEB APPLICATIONS'

const titles = [
  'FRONTEND DEVELOPER',
  'UI/UX ENTHUSIAST',
  'OPEN SOURCE DEV',
  'TECH WRITER'
]

const nameChars = 'YAN PHAYU'.split('')

let index = 0
let charIndex = 0
let isDeleting = false

function scrollTo(id) {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' })
}

function typeLoop() {
  const current = titles[index]
  if (!isDeleting) {
    displayText.value = current.slice(0, charIndex + 1)
    charIndex++
    if (charIndex === current.length) {
      setTimeout(() => { isDeleting = true; typeLoop() }, 2500)
      return
    }
  } else {
    displayText.value = current.slice(0, charIndex - 1)
    charIndex--
    if (charIndex === 0) {
      isDeleting = false
      index = (index + 1) % titles.length
    }
  }
  const delay = isDeleting ? 30 : 80
  setTimeout(typeLoop, delay)
}

const avatar = [
  '.....XXXXX.....'.split(''),
  '....XXYYYXX....'.split(''),
  '...XXXXXXXXX...'.split(''),
  '..XXXYYYXXXXX..'.split(''),
  '..XXXXXXXXXXX..'.split(''),
  '..XXYYYXXYYXX..'.split(''),
  '..XX.YXX.YXX...'.split(''),
  '..XXXXXXXXXX...'.split(''),
  '...XX.XX.XX....'.split(''),
  '...XXXXXXXXX...'.split(''),
  '...XXXXXXXXX...'.split(''),
  '..XX......XX...'.split(''),
  '..X........X...'.split(''),
]

onMounted(() => {
  setTimeout(typeLoop, 1000)
})
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 6rem 2rem;
  color: #c8c8d4;
  text-align: center;
}

.hero-content {
  max-width: 700px;
  width: 100%;
}

.pixel-badge {
  font-size: 0.75rem;
  color: #ffcc00;
  border: 3px solid #ffcc00;
  padding: 0.5rem 1rem;
  display: inline-block;
  margin-bottom: 2.5rem;
  letter-spacing: 3px;
  animation: blink 1.2s step-end infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.3; }
}

.pixel-avatar {
  margin: 0 auto 2rem;
  width: 220px;
}

.pixel-row {
  display: flex;
  justify-content: center;
}

.pixel {
  width: 14px;
  height: 14px;
}

.pixel.x { background: #ffcc00; }
.pixel.y { background: #ff6b6b; }
.pixel.e { background: transparent; }

h1 {
  font-size: 2.5rem;
  color: #fff;
  margin-bottom: 1.2rem;
  letter-spacing: 6px;
  word-break: break-word;
}

.char {
  display: inline-block;
  animation: pop 0.4s ease both;
}

@keyframes pop {
  0% { transform: scale(0); opacity: 0; }
  60% { transform: scale(1.2); }
  100% { transform: scale(1); opacity: 1; }
}

.subtitle {
  font-size: 0.85rem;
  color: rgba(200, 200, 212, 0.6);
  margin-bottom: 0.8rem;
  min-height: 1.6rem;
  letter-spacing: 2px;
}

.cursor {
  animation: blink-cursor 1s step-end infinite;
  color: #ffcc00;
}

@keyframes blink-cursor {
  50% { opacity: 0; }
}

.tagline {
  font-size: 0.6rem;
  color: rgba(200, 200, 212, 0.3);
  margin-bottom: 3rem;
  letter-spacing: 2px;
  line-height: 2;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
}

.hero-btns {
  display: flex;
  gap: 1.2rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  padding: 0;
  font-size: 0.7rem;
  text-decoration: none;
  transition: all 0.15s;
  cursor: pointer;
  font-family: 'Press Start 2P', monospace;
  letter-spacing: 2px;
  position: relative;
}

.btn-pixel {
  position: relative;
  background: #ffcc00;
  color: #1a1a2e;
  border: none;
  box-shadow: 4px 4px 0 0 #b38a00;
  padding: 0.9rem 1.8rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.btn-pixel:active {
  transform: translate(2px, 2px);
  box-shadow: 1px 1px 0 0 #b38a00;
}

.btn-pixel-outline {
  position: relative;
  background: transparent;
  color: #ffcc00;
  border: 3px solid #ffcc00;
  padding: 0.9rem 1.8rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.btn-pixel-outline:hover {
  background: rgba(255, 204, 0, 0.08);
}

/* Tablet */
@media (max-width: 768px) {
  .hero {
    padding: 5rem 1.5rem 7rem;
  }
  .pixel-avatar {
    width: 165px;
  }
  .pixel {
    width: 11px;
    height: 11px;
  }
  h1 {
    font-size: 1.8rem;
    letter-spacing: 4px;
  }
  .subtitle {
    font-size: 0.65rem;
  }
  .tagline {
    font-size: 0.5rem;
  }
  .btn {
    font-size: 0.55rem;
  }
  .btn-pixel, .btn-pixel-outline {
    padding: 0.7rem 1.4rem;
  }
  .pixel-badge {
    font-size: 0.6rem;
    padding: 0.4rem 0.8rem;
    margin-bottom: 2rem;
  }
}

/* Phone */
@media (max-width: 480px) {
  .hero {
    padding: 4rem 1rem 6rem;
  }
  .pixel-avatar {
    width: 120px;
  }
  .pixel {
    width: 8px;
    height: 8px;
  }
  h1 {
    font-size: 1.2rem;
    letter-spacing: 3px;
  }
  .subtitle {
    font-size: 0.5rem;
    letter-spacing: 1px;
  }
  .tagline {
    font-size: 0.38rem;
    letter-spacing: 1px;
    margin-bottom: 2rem;
  }
  .hero-btns {
    gap: 0.8rem;
  }
  .btn {
    font-size: 0.45rem;
  }
  .btn-pixel, .btn-pixel-outline {
    padding: 0.6rem 1rem;
    box-shadow: 3px 3px 0 0 #b38a00;
  }
  .pixel-badge {
    font-size: 0.45rem;
    padding: 0.3rem 0.6rem;
    margin-bottom: 1.5rem;
    border-width: 2px;
  }
}

/* Tiny / Watch */
@media (max-width: 360px) {
  .hero {
    padding: 3rem 0.6rem 5rem;
    min-height: 90vh;
  }
  .pixel-avatar {
    width: 90px;
  }
  .pixel {
    width: 6px;
    height: 6px;
  }
  h1 {
    font-size: 0.85rem;
    letter-spacing: 2px;
  }
  .subtitle {
    font-size: 0.38rem;
  }
  .tagline {
    font-size: 0.3rem;
  }
  .btn {
    font-size: 0.35rem;
  }
  .btn-pixel, .btn-pixel-outline {
    padding: 0.45rem 0.7rem;
    box-shadow: 2px 2px 0 0 #b38a00;
  }
  .btn-pixel:active {
    transform: translate(1px, 1px);
    box-shadow: 1px 1px 0 0 #b38a00;
  }
  .pixel-badge {
    font-size: 0.35rem;
    padding: 0.25rem 0.5rem;
    margin-bottom: 1rem;
  }
}
</style>
