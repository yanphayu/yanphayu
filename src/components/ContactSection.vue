<template>
  <section id="contact" class="contact">
    <div class="section-header">
      <span class="section-bar"></span>
      <h2>CONTACT</h2>
      <span class="section-bar"></span>
    </div>
    <p class="section-sub">OPEN FOR PROJECTS AND COLLABORATIONS</p>

    <form class="contact-form" @submit.prevent="handleSubmit">
      <div class="form-row">
        <input
          v-model="form.name"
          type="text"
          placeholder="NAME"
          required
          autocomplete="off"
        />
        <input
          v-model="form.email"
          type="email"
          placeholder="EMAIL"
          required
          autocomplete="off"
        />
      </div>
      <textarea
        v-model="form.message"
        rows="4"
        placeholder="MESSAGE"
        required
      ></textarea>

      <div class="form-actions">
        <button type="submit" class="btn btn-pixel" :disabled="submitting">
          <span class="btn-text">{{ submitting ? 'SENDING...' : 'SEND MSG' }}</span>
        </button>
        <p v-if="submitted" class="success-msg">SENT!</p>
      </div>
    </form>

    <p class="contact-note">AVAILABLE FOR FREELANCE, FULL-TIME, AND CONSULTING</p>
    <div class="social-links">
      <a href="https://www.tiktok.com/@yukkkkkkkkkkk.1" target="_blank">
        <abbr data-title="TIKTOK">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
            <rect x="2" y="2" width="24" height="24" fill="none" stroke="#ffcc00" stroke-width="2"/>
            <path d="M11 20V10c0-2 3-4 6-2v2c-1 0-2 1-2 2v8" stroke="#ffcc00" stroke-width="2" stroke-linecap="square"/>
            <circle cx="9" cy="18" r="2" fill="none" stroke="#ffcc00" stroke-width="2"/>
            <path d="M15 14c2 1 4 0 5-2" stroke="#ffcc00" stroke-width="2" stroke-linecap="square"/>
          </svg>
        </abbr>
      </a>
      <a href="https://t.me/+F0WtousuDAFiNjI1" target="_blank">
        <abbr data-title="TELEGRAM">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
            <rect x="2" y="2" width="24" height="24" fill="none" stroke="#48dbfb" stroke-width="2"/>
            <path d="M6 14l6-3 10-5-5 10-3 3-2-5-6-2z" fill="none" stroke="#48dbfb" stroke-width="2" stroke-linejoin="miter"/>
            <path d="M12 17l10-11" stroke="#48dbfb" stroke-width="2" stroke-linecap="square"/>
          </svg>
        </abbr>
      </a>
      <a href="https://www.facebook.com/share/1BPaWbximo/?mibextid=wwXIfr" target="_blank">
        <abbr data-title="FACEBOOK">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
            <rect x="2" y="2" width="24" height="24" fill="none" stroke="#48dbfb" stroke-width="2"/>
            <path d="M14 4v12M14 16h-4M14 16h4v6" stroke="#48dbfb" stroke-width="2" stroke-linecap="square"/>
            <circle cx="14" cy="22" r="2" fill="none" stroke="#48dbfb" stroke-width="2"/>
          </svg>
        </abbr>
      </a>
      <a href="https://www.youtube.com/@YukkkCoder" target="_blank">
        <abbr data-title="YOUTUBE">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
            <rect x="2" y="2" width="24" height="24" fill="none" stroke="#ff6b6b" stroke-width="2"/>
            <rect x="5" y="10" width="18" height="10" fill="none" stroke="#ff6b6b" stroke-width="2"/>
            <path d="M12 12l5 3-5 3V12z" fill="rgba(255,107,107,0.15)" stroke="#ff6b6b" stroke-width="1.5" stroke-linejoin="miter"/>
          </svg>
        </abbr>
      </a>
      <a href="https://github.com/yanphayu" target="_blank">
        <abbr data-title="GITHUB">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
            <rect x="2" y="2" width="24" height="24" fill="none" stroke="#c8c8d4" stroke-width="2"/>
            <circle cx="14" cy="12" r="6" stroke="#c8c8d4" stroke-width="2"/>
            <path d="M14 18v4M10 22h8" stroke="#c8c8d4" stroke-width="2" stroke-linecap="square"/>
            <path d="M9 13c-1 1-1 3 0 4" stroke="#c8c8d4" stroke-width="1.5" stroke-linecap="square"/>
            <path d="M19 13c1 1 1 3 0 4" stroke="#c8c8d4" stroke-width="1.5" stroke-linecap="square"/>
          </svg>
        </abbr>
      </a>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue'

const form = reactive({ name: '', email: '', message: '' })
const submitting = ref(false)
const submitted = ref(false)

function handleSubmit() {
  submitting.value = true
  setTimeout(() => {
    submitting.value = false
    submitted.value = true
    form.name = ''
    form.email = ''
    form.message = ''
    setTimeout(() => { submitted.value = false }, 4000)
  }, 1200)
}
</script>

<style scoped>
.contact {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 6rem 2rem;
  color: #c8c8d4;
  text-align: center;
}

.section-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 0.5rem;
}

.section-bar {
  display: inline-block;
  width: 32px;
  height: 4px;
  background: #ffcc00;
  flex-shrink: 0;
}

h2 {
  font-size: 1.6rem;
  color: #fff;
  letter-spacing: 4px;
}

.section-sub {
  color: rgba(200, 200, 212, 0.3);
  margin-bottom: 3rem;
  font-size: 0.55rem;
  letter-spacing: 3px;
}

.contact-form {
  width: 100%;
  max-width: 520px;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.form-row {
  display: flex;
  gap: 1rem;
}

.form-row input {
  flex: 1;
}

.contact-form input,
.contact-form textarea {
  width: 100%;
  padding: 0.9rem 1rem;
  border: 3px solid #16213e;
  background: rgba(255, 255, 255, 0.02);
  color: #c8c8d4;
  font-size: 0.6rem;
  font-family: 'Press Start 2P', monospace;
  transition: background-color 5000s ease-in-out 0s;
  outline: none;
  -webkit-text-fill-color: #c8c8d4;
  caret-color: #ffcc00;
  letter-spacing: 1.5px;
}

.contact-form input:focus,
.contact-form textarea:focus {
  border-color: #ffcc00;
}

.contact-form input:-webkit-autofill,
.contact-form input:-webkit-autofill:hover,
.contact-form input:-webkit-autofill:focus,
.contact-form input:-webkit-autofill:active {
  -webkit-box-shadow: 0 0 0 1000px #1a1a2e inset !important;
  -webkit-text-fill-color: #c8c8d4 !important;
  border: 3px solid #ffcc00;
}

.contact-form input::placeholder,
.contact-form textarea::placeholder {
  color: rgba(200, 200, 212, 0.15);
  font-family: 'Press Start 2P', monospace;
  font-size: 0.6rem;
}

.contact-form textarea {
  resize: vertical;
}

.form-actions {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.btn {
  padding: 0;
  font-size: 0.65rem;
  text-decoration: none;
  transition: all 0.15s;
  cursor: pointer;
  font-family: 'Press Start 2P', monospace;
  letter-spacing: 2px;
  border: none;
}

.btn-pixel {
  background: #ffcc00;
  color: #1a1a2e;
  box-shadow: 4px 4px 0 0 #b38a00;
  padding: 0.85rem 1.5rem;
}

.btn-pixel:active {
  transform: translate(2px, 2px);
  box-shadow: 1px 1px 0 0 #b38a00;
}

.btn-pixel:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
  box-shadow: 1px 1px 0 0 #b38a00;
}

.success-msg {
  font-size: 0.55rem;
  color: #ffcc00;
  animation: blink 0.8s step-end infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

.contact-note {
  font-size: 0.5rem;
  color: rgba(200, 200, 212, 0.2);
  margin-bottom: 2rem;
  letter-spacing: 2px;
}

.social-links {
  display: flex;
  gap: 0.8rem;
  flex-wrap: wrap;
  justify-content: center;
}

.social-links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  border: 3px solid #16213e;
  transition: all 0.15s;
  background: rgba(255, 255, 255, 0.02);
}

.social-links a abbr {
  border-bottom: none;
}

.social-links a svg {
  transition: transform 0.15s;
}

.social-links a:hover {
  border-color: #ffcc00;
  background: rgba(255, 204, 0, 0.08);
}

.social-links a:hover svg {
  transform: scale(1.15);
}

@media (max-width: 768px) {
  .contact { padding: 5rem 1.5rem 7rem; }
  h2 { font-size: 1.2rem; }
  .section-bar { width: 24px; }
  .section-sub { font-size: 0.45rem; }
  .contact-form input, .contact-form textarea { font-size: 0.5rem; padding: 0.7rem 0.8rem; }
  .contact-form input::placeholder, .contact-form textarea::placeholder { font-size: 0.5rem; }
  .btn { font-size: 0.5rem; }
  .btn-pixel { padding: 0.65rem 1.2rem; }
}

@media (max-width: 480px) {
  .contact { padding: 4rem 1rem 6rem; }
  .section-header { gap: 0.6rem; }
  h2 { font-size: 0.9rem; letter-spacing: 2px; }
  .section-bar { width: 16px; height: 3px; }
  .section-sub { font-size: 0.38rem; margin-bottom: 2rem; }
  .form-row { flex-direction: column; gap: 0.8rem; }
  .contact-form input, .contact-form textarea {
    font-size: 0.4rem; padding: 0.6rem; border-width: 2px;
  }
  .contact-form input::placeholder, .contact-form textarea::placeholder { font-size: 0.4rem; }
  .btn { font-size: 0.42rem; }
  .btn-pixel { padding: 0.55rem 1rem; box-shadow: 3px 3px 0 0 #b38a00; }
  .contact-note { font-size: 0.38rem; }
  .social-links { gap: 0.6rem; }
  .social-links a { width: 42px; height: 42px; border-width: 2px; }
  .social-links a svg { width: 24px; height: 24px; }
}

@media (max-width: 360px) {
  .contact { padding: 3rem 0.6rem 5rem; }
  .section-header { gap: 0.4rem; }
  h2 { font-size: 0.65rem; }
  .section-bar { width: 12px; height: 2px; }
  .section-sub { font-size: 0.28rem; }
  .contact-form { gap: 0.6rem; }
  .contact-form input, .contact-form textarea { font-size: 0.32rem; padding: 0.5rem; }
  .contact-form input::placeholder, .contact-form textarea::placeholder { font-size: 0.32rem; }
  .btn { font-size: 0.35rem; }
  .btn-pixel { padding: 0.4rem 0.7rem; box-shadow: 2px 2px 0 0 #b38a00; }
  .contact-note { font-size: 0.3rem; }
  .social-links { gap: 0.4rem; }
  .social-links a { width: 36px; height: 36px; border-width: 2px; }
  .social-links a svg { width: 20px; height: 20px; }
}
</style>
