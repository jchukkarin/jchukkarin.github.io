<script setup>
import { RouterLink } from 'vue-router'
import { ref, onMounted } from 'vue'

const isDark = ref(false)
const mobileOpen = ref(false)

const setTheme = (dark) => {
  isDark.value = dark
  document.documentElement.classList.toggle('dark', dark)
  localStorage.setItem('theme', dark ? 'dark' : 'light')
}

const toggleTheme = () => setTheme(!isDark.value)
const toggleMobile = () => (mobileOpen.value = !mobileOpen.value)

onMounted(() => {
  const saved = localStorage.getItem('theme')
  if (saved) {
    setTheme(saved === 'dark')
  } else {
    // Auto detect theme เครื่อง
    const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches
    setTheme(prefersDark)
  }
})
</script>

<template>
  <nav :class="['navbar', isDark ? 'dark' : 'light']">
    <div class="container">
      <!-- Logo -->
      <RouterLink class="logo">
        <span class="circle">Portfolio</span>
      </RouterLink>

      <!-- Menu -->
      <div class="menu">
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#skills-section">Skills</a>
        <a href="#experience">Experience</a>
        <a href="#certificates">Certifications</a>
        <a href="#contact">Contact</a>
      </div>

      <!-- Right -->
      <div class="actions">
        <div class="toggle-container">
          <span>Dark Mode</span>

          <label class="switch">
            <input type="checkbox" :checked="isDark" @change="toggleTheme" />
            <span class="slider"></span>
          </label>
        </div>

        <a href="/Resume-Chukkarin.pdf" download class="btn">Download CV</a>

        <button class="mobile-btn" @click="toggleMobile">☰</button>
      </div>
    </div>

    <!-- Mobile -->
    <div v-if="mobileOpen" class="mobile-menu">
      <RouterLink to="/about" @click="mobileOpen = false">About</RouterLink>
      <a href="#home">Home</a>
      <a href="#about">About</a>
      <a href="#skills-section">Skills</a>
      <a href="#experience">Experience</a>
      <a href="#certificates">Certifications</a>
      <a href="#contact">Contact</a>
    </div>
  </nav>
</template>

<style scoped>
/* Navbar */
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  border-bottom: 1px solid #ddd;
  z-index: 1000;
  transition: 0.3s;
}

/* Theme */
.navbar {
  background: var(--bg);
  color: var(--text);
  border-bottom: 1px solid var(--border);
}

/* Layout */
.container {
  max-width: 1200px;
  margin: auto;
  padding: 10px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* Logo */
.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: bold;
  text-decoration: none;
  color: inherit;
}

.circle {
  width: 240px;
  height: 60px;
  font-size: 48px;
  border-radius: 20px;
  background: var(--primary);
  color: var(--bg);
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Menu */
.menu {
  display: flex;
  gap: 20px;
}

.menu a {
  text-decoration: none;
  color: inherit;
}

.menu a.active {
  font-weight: bold;
}

/* Actions */
.actions {
  display: flex;
  align-items: center;
  gap: 10px;
}

.btn {
  padding: 6px 12px;
  background: var(--primary);
  color: var(--bg);
  border-radius: 20px;
  text-decoration: none;
}

/* Mobile */
.mobile-btn {
  display: none;
}

.mobile-menu {
  padding: 10px 20px;
  border-top: 1px solid #ddd;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

/* Responsive */
@media (max-width: 768px) {
  .menu {
    display: none;
  }

  .mobile-btn {
    display: block;
  }
}

/* Container */
.toggle-container {
  display: flex;
  align-items: center;
  gap: 10px;
}

/* Switch */
.switch {
  position: relative;
  width: 50px;
  height: 25px;
}

/* Hide default checkbox */
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

/* Slider */
.slider {
  position: absolute;
  cursor: pointer;
  inset: 0;
  background-color: #ccc;
  border-radius: 25px;
  transition: 0.3s;
}

/* Circle */
.slider::before {
  content: '';
  position: absolute;
  height: 20px;
  width: 20px;
  left: 3px;
  top: 2.5px;
  background-color: white;
  border-radius: 50%;
  transition: 0.3s;
}

/* Checked */
.switch input:checked + .slider {
  background-color: #4f46e5;
}

.switch input:checked + .slider::before {
  transform: translateX(24px);
}
</style>
