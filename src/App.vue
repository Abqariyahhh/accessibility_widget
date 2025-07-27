<template>
  <div id="app">
    <FloatingButton @toggle-menu="menuOpen = !menuOpen" />
    <MenuPanel v-if="menuOpen"
      :contrast="contrast"
      :biggerText="biggerText"
      :dyslexia="dyslexia"
      :hideImages="hideImages"
      :highlightLinks="highlightLinks"
      :textSpacing="textSpacing"
      :pauseAnimations="pauseAnimations"
      :pageStructure="pageStructure"
      :colorBlind="colorBlind"
      @toggle-contrast="toggleContrast"
      @toggle-text-size="toggleTextSize"
      @toggle-dyslexia="toggleDyslexia"
      @toggle-hide-images="toggleHideImages"
      @toggle-highlight-links="toggleHighlightLinks"
      @toggle-text-spacing="toggleTextSpacing"
      @toggle-pause-animations="togglePauseAnimations"
      @toggle-page-structure="togglePageStructure"
      @toggle-color-blind="toggleColorBlind"
    />
    <div class="content-container">
      <main>
        <h1>Welcome to Accessibility Widget Demo</h1>
        <h2>Heading Level 2</h2>
        <p>This is sample text for testing accessibility options like text size, spacing, dyslexia-friendly font, color blindness mode, and more.</p>
        <a href="#">Sample Link</a>
        <div class="animated-box"></div>
        <img class="demo-image"
             src="https://images.unsplash.com/photo-1503023345310-bd7c1de61c7d"
             alt="Nature Photo" />
      </main>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import FloatingButton from './components/FloatingButton.vue'
import MenuPanel from './components/MenuPanel.vue'

const menuOpen = ref(false)
const contrast = ref(false)
const biggerText = ref(false)
const dyslexia = ref(false)
const hideImages = ref(false)
const highlightLinks = ref(false)
const textSpacing = ref(false)
const pauseAnimations = ref(false)
const pageStructure = ref(false)
const colorBlind = ref(false)

onMounted(() => {
  if (localStorage.getItem('contrast') === 'true') {
    contrast.value = true
    document.querySelector('.content-container')?.classList.add('high-contrast')
  }
  if (localStorage.getItem('biggerText') === 'true') {
    biggerText.value = true
    document.documentElement.style.setProperty('--base-font-size', '20px')
  }
  if (localStorage.getItem('dyslexia') === 'true') {
    dyslexia.value = true
    loadDyslexicFont()
    document.body.classList.add('dyslexia')
  }
  if (localStorage.getItem('hideImages') === 'true') {
    hideImages.value = true
    document.body.classList.add('hide-images')
  }
  if (localStorage.getItem('highlightLinks') === 'true') {
    highlightLinks.value = true
    document.body.classList.add('highlight-links')
  }
  if (localStorage.getItem('textSpacing') === 'true') {
    textSpacing.value = true
    document.body.classList.add('text-spacing')
  }
  if (localStorage.getItem('pauseAnimations') === 'true') {
    pauseAnimations.value = true
    enablePauseAnimations(true)
  }
  if (localStorage.getItem('pageStructure') === 'true') {
    pageStructure.value = true
    document.body.classList.add('show-structure')
  }
  if (localStorage.getItem('colorBlind') === 'true') {
    colorBlind.value = true
    document.querySelector('.content-container')?.classList.add('color-blind')
  }
})

function toggleContrast() {
  contrast.value = !contrast.value
  document.querySelector('.content-container')?.classList.toggle('high-contrast', contrast.value)
  localStorage.setItem('contrast', contrast.value)
}
function toggleTextSize() {
  biggerText.value = !biggerText.value
  const size = biggerText.value ? '20px' : '16px'
  document.documentElement.style.setProperty('--base-font-size', size)
  localStorage.setItem('biggerText', biggerText.value)
}
function toggleDyslexia() {
  dyslexia.value = !dyslexia.value
  if (dyslexia.value) loadDyslexicFont()
  document.body.classList.toggle('dyslexia', dyslexia.value)
  localStorage.setItem('dyslexia', dyslexia.value)
}
function toggleHideImages() {
  hideImages.value = !hideImages.value
  document.body.classList.toggle('hide-images', hideImages.value)
  localStorage.setItem('hideImages', hideImages.value)
}
function toggleHighlightLinks() {
  highlightLinks.value = !highlightLinks.value
  document.body.classList.toggle('highlight-links', highlightLinks.value)
  localStorage.setItem('highlightLinks', highlightLinks.value)
}
function toggleTextSpacing() {
  textSpacing.value = !textSpacing.value
  document.body.classList.toggle('text-spacing', textSpacing.value)
  localStorage.setItem('textSpacing', textSpacing.value)
}
function togglePauseAnimations() {
  pauseAnimations.value = !pauseAnimations.value
  enablePauseAnimations(pauseAnimations.value)
  localStorage.setItem('pauseAnimations', pauseAnimations.value)
}
function togglePageStructure() {
  pageStructure.value = !pageStructure.value
  document.body.classList.toggle('show-structure', pageStructure.value)
  localStorage.setItem('pageStructure', pageStructure.value)
}
function toggleColorBlind() {
  colorBlind.value = !colorBlind.value
  document.querySelector('.content-container')?.classList.toggle('color-blind', colorBlind.value)
  localStorage.setItem('colorBlind', colorBlind.value)
}

function enablePauseAnimations(enable) {
  let style = document.getElementById('pause-style')
  if (enable) {
    if (!style) {
      style = document.createElement('style')
      style.id = 'pause-style'
      style.innerHTML = `
        *, *::before, *::after {
          animation-play-state: paused !important;
          transition: none !important;
        }
        html, body {
          scroll-behavior: auto !important;
        }
      `
      document.head.appendChild(style)
    }
  } else {
    if (style) style.remove()
  }
}
function loadDyslexicFont() {
  if (!document.getElementById('dyslexic-font')) {
    const link = document.createElement('link')
    link.id = 'dyslexic-font'
    link.rel = 'stylesheet'
    link.href = 'https://fonts.googleapis.com/css2?family=Atkinson+Hyperlegible&display=swap'
    document.head.appendChild(link)
  }
}
</script>

<style>
:root { --base-font-size: 16px; }
body { font-size: var(--base-font-size); font-family: Arial, sans-serif; }
body.dyslexia { font-family: 'Atkinson Hyperlegible', Arial, sans-serif !important; }
body.hide-images img { visibility: hidden !important; }
body.highlight-links a { border-bottom: 2px solid #ff0000; padding-bottom: 2px; }
body.text-spacing { letter-spacing: 0.12rem !important; line-height: 1.8 !important; }

/* Filters only on content */
.content-container.high-contrast { filter: contrast(120%); }
.content-container.color-blind { filter: grayscale(50%) contrast(120%); }

/* Page Structure */
body.show-structure h1,
body.show-structure h2,
body.show-structure h3,
body.show-structure h4,
body.show-structure h5,
body.show-structure h6 {
  outline: 2px dashed #ff6600;
  outline-offset: 4px;
}

.demo-image {
  width: 600px;
  max-width: 100%;
  height: auto;
  display: block;
  margin-top: 85px;
  margin-left: 210px;
  animation: imageZoom 2s infinite alternate ease-in-out;
}
@keyframes imageZoom {
  from { transform: scale(1); }
  to { transform: scale(1.15); }
}
main { padding: 2rem; }
</style>
