<template>
  <div class="menu-panel">
    <h2>Accessibility Options</h2>
    <div class="option">
      <input type="checkbox" id="contrast" :checked="contrast" @change="$emit('toggle-contrast')" />
      <label for="contrast">High Contrast</label>
    </div>
    <div class="option">
      <input type="checkbox" id="biggerText" :checked="biggerText" @change="$emit('toggle-text-size')" />
      <label for="biggerText">Bigger Text</label>
    </div>
    <div class="option">
      <input type="checkbox" id="dyslexia" :checked="dyslexia" @change="$emit('toggle-dyslexia')" />
      <label for="dyslexia">Dyslexia-Friendly Font</label>
    </div>
    <div class="option">
      <input type="checkbox" id="hideImages" :checked="hideImages" @change="$emit('toggle-hide-images')" />
      <label for="hideImages">Hide Images</label>
    </div>
    <div class="option">
      <input type="checkbox" id="highlightLinks" :checked="highlightLinks" @change="$emit('toggle-highlight-links')" />
      <label for="highlightLinks">Highlight Links</label>
    </div>
    <div class="option">
      <input type="checkbox" id="textSpacing" :checked="textSpacing" @change="$emit('toggle-text-spacing')" />
      <label for="textSpacing">Text Spacing</label>
    </div>
    <div class="option">
      <input type="checkbox" id="pauseAnimations" :checked="pauseAnimations" @change="$emit('toggle-pause-animations')" />
      <label for="pauseAnimations">Pause Animations</label>
    </div>
    <div class="option">
      <input type="checkbox" id="pageStructure" :checked="pageStructure" @change="$emit('toggle-page-structure')" />
      <label for="pageStructure">Show Page Structure</label>
    </div>
    <div class="option">
      <input type="checkbox" id="colorBlind" :checked="colorBlind" @change="$emit('toggle-color-blind')" />
      <label for="colorBlind">Color Blind Mode</label>
    </div>
  </div>
</template>

<script setup>
defineProps([
  'contrast', 'biggerText', 'dyslexia', 'hideImages',
  'highlightLinks', 'textSpacing', 'pauseAnimations',
  'pageStructure', 'colorBlind'
])
</script>

<style scoped>
.menu-panel {
  position: fixed;
  bottom: 100px;
  right: 24px;
  width: 280px;
  background: #ffffff;
  border-radius: 12px;
  padding: 1.2rem;
  box-shadow: 0 4px 16px rgba(0,0,0,0.2);
  z-index: 9999;
  font-family: 'Segoe UI', sans-serif;
  animation: slideIn 0.3s ease-out;
}
@keyframes slideIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
h2 { font-size: 1.3rem; font-weight: 600; margin-bottom: 1rem; color: #333; }
.option { display: flex; align-items: center; margin-bottom: 0.8rem; }
.option label { margin-left: 8px; font-size: 1rem; cursor: pointer; }
input[type="checkbox"] { width: 18px; height: 18px; accent-color: #007bff; }
</style>
