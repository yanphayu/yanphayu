<template>
  <footer>
    <div class="footer-pixel"></div>
    <p>&copy; 2026 YAN PHAYU // BUILT WITH VUE & VITE</p>
  </footer>
</template>

<style scoped>
footer {
  padding: 2rem;
  text-align: center;
}

.footer-pixel {
  width: 32px;
  height: 4px;
  background: #ffcc00;
  margin: 0 auto 1rem;
}

footer p {
  color: rgba(200, 200, 212, 0.1);
  font-size: 0.45rem;
  letter-spacing: 3px;
}

@media (max-width: 768px) {
  footer { padding: 1.5rem; }
  footer p { font-size: 0.35rem; }
}

@media (max-width: 480px) {
  footer { padding: 1rem 1rem 5rem; }
  .footer-pixel { width: 24px; height: 3px; }
  footer p { font-size: 0.28rem; letter-spacing: 2px; }
}

@media (max-width: 360px) {
  footer { padding: 0.8rem 0.6rem 4rem; }
  footer p { font-size: 0.22rem; }
}
</style>
