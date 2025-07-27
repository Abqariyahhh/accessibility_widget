<template>
  <button class="floating-btn" @click="$emit('toggle-menu')" aria-label="Accessibility Options">
    <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="white">
      <path d="M12 2C6.477 2 2 6.477 2 12c0 4.56 3.064 8.385 7.23 9.54.53.097.72-.23.72-.51v-1.79c-2.94.64-3.56-1.42-3.56-1.42-.48-1.21-1.17-1.53-1.17-1.53-.95-.65.07-.63.07-.63 1.05.07 1.6 1.09 1.6 1.09.94 1.6 2.46 1.14 3.06.87.1-.68.37-1.14.67-1.4-2.35-.26-4.82-1.18-4.82-5.23 0-1.16.42-2.1 1.1-2.84-.11-.27-.48-1.37.1-2.85 0 0 .89-.28 2.9 1.08a10.06 10.06 0 0 1 2.64-.35c.9.01 1.82.12 2.64.35 2-1.36 2.9-1.08 2.9-1.08.58 1.48.21 2.58.1 2.85.69.74 1.1 1.68 1.1 2.84 0 4.06-2.47 4.97-4.83 5.23.38.33.73.98.73 1.98v2.94c0 .28.19.61.73.5C18.94 20.38 22 16.56 22 12c0-5.523-4.477-10-10-10z"/>
    </svg>
  </button>
</template>

<style scoped>
.floating-btn {
  position: fixed;
  bottom: 24px;
  right: 24px;
  border-radius: 50%;
  width: 64px;
  height: 64px;
  background: linear-gradient(135deg, #007bff, #00b4d8);
  color: white;
  border: none;
  cursor: pointer;
  z-index: 9999;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.25);
  transition: transform 0.2s ease-in-out, box-shadow 0.2s;
}
.floating-btn:focus {
  outline: none;
}
.floating-btn:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.35);
}
</style>
