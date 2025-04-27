<template>
  <div class="navbar-container">
    <nav class="navbar">
      <router-link to="/" class="nav-brand">
        <!-- <img src="../assets/sw11.png" alt="Logo" class="nav-logo" /> -->
      </router-link>

      <div class="nav-links" :class="{ show: isMenuVisible }" ref="navLinks">
        <a href="#page" class="nav-link">à propos de nous</a>
        <a href="#toteee" class="nav-link">nos services</a>
        <a href="#pa" class="nav-link">nos projets</a>
      </div>

      <router-link to="" class="nav-cta">
        <button class="cta-button">Demande devis</button>
      </router-link>

      <div class="menu-icon" @click="toggleMenu" ref="menuIcon">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </div>
    </nav>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const isMenuVisible = ref(false)
const menuIcon = ref(null)
const navLinks = ref(null)

const toggleMenu = () => {
  isMenuVisible.value = !isMenuVisible.value
}

const hideMenuOnClickOutside = (event) => {
  if (
    navLinks.value &&
    menuIcon.value &&
    !navLinks.value.contains(event.target) &&
    !menuIcon.value.contains(event.target)
  ) {
    isMenuVisible.value = false
  }
}

onMounted(() => {
  document.addEventListener('click', hideMenuOnClickOutside)
})

onBeforeUnmount(() => {
  document.removeEventListener('click', hideMenuOnClickOutside)
})
</script>

<style scoped>
.navbar-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1;
  background: rgba(26, 26, 46, 0.95);
  backdrop-filter: blur(10px);
  margin-left: 8px;
  margin-right: 10%;


}

.navbar {
   /* <<< réduit encore plus la largeur */
  margin-right:  10px ;
  padding: 10px; /* petit padding */
  height: 50px; /* hauteur fixée */
  display: flex;
  position: relative;
  align-items: center;
  justify-content: space-between;
}

.nav-brand {
  display: flex;
  align-items: center;
}


.nav-logo {
  width: 36px; /* <<< plus petit */
  height: 36px;
  object-fit: contain;
}

.nav-links {
  display: flex;
  gap: 1.5rem; /* <<< réduit l'espacement */
  margin: 0 1rem;
}

.nav-link {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem; /* <<< réduit la taille du texte */
  transition: all 0.3s ease;
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: #64ffda;
  transition: width 0.3s ease;
}

.nav-link:hover {
  color: #64ffda;
}

.nav-link:hover::after {
  width: 100%;
}

.cta-button {
  padding: 0.5rem 1rem; /* <<< réduit le bouton */
  border-radius: 25px;
  background: linear-gradient(45deg, #64ffda, #0891b2);
  border: none;
  color: white;
  font-weight: 600;
  font-size: 0.95rem; /* <<< plus petit */
  cursor: pointer;
  transition: all 0.3s ease;
}

.cta-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(100, 255, 218, 0.2);
}

.menu-icon {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
  padding: 2px;
}

.menu-icon .bar {
  width: 24px; /* <<< réduit */
  height: 2px;
  background: #64ffda;
  transition: all 0.3s ease;
}

@media (max-width: 1024px) {
  .nav-links {
    position: fixed;
    top: 60px; /* <<< adapté */
    left: 0;
    width: 100%;
    background: rgba(26, 26, 46, 0.98);
    padding: 1.5rem;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    transform: translateY(-150%);
    opacity: 0;
    transition: all 0.3s ease;
    pointer-events: none;
  }

  .nav-links.show {
    transform: translateY(0);
    opacity: 1;
    pointer-events: all;
  }

  .menu-icon {
    display: flex;
  }
}

@media (max-width: 768px) {
  .navbar {
    padding: 0.5rem;
  }

  .nav-logo {
    width: 32px;
    height: 32px;
  }

  .cta-button {
    display: none;
  }
}
</style>
