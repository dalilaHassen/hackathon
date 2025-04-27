<template>
  <section class="hero-section">
    <div class="particles-container">
      <div v-for="n in 20" :key="n" class="particle"></div>
    </div>

    <div class="hero-content" :class="{ 'visible': isVisible }">
      <div class="hero-text-container">
        <h1 class="hero-title">{{ title }}</h1>
        <p class="hero-text">
          Transformez votre entreprise avec notre expertise fiable et innovante.
          <br><br>
          Nous simplifions et accélérons votre parcours de transformation numérique,
          vous permettant de relever les défis de l'ère digitale.
        </p>
        <div class="button-container">
          <button class="cta-button primary">Découvrir nos services</button>
          <button class="cta-button secondary">Contactez-nous</button>
        </div>
      </div>

      <div class="hero-visual">
        <div class="geometric-shape"></div>
        <div class="floating-elements">
          <div class="float-item" v-for="n in 5" :key="'float-' + n"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import gsap from 'gsap'

export default {
  name: 'HeroSection',
  data() {
    return {
      title: 'Réalisons vos Ambitions Numériques',
      isVisible: false,
    }
  },
  mounted() {
    this.isVisible = true;

    // Animation des particules
    const particles = gsap.utils.toArray('.particle');
    particles.forEach(particle => {
      gsap.to(particle, {
        x: 'random(-100, 100)',
        y: 'random(-100, 100)',
        rotation: 'random(-180, 180)',
        duration: 'random(3, 6)',
        repeat: -1,
        yoyo: true,
        ease: 'none'
      });
    });

    // Animation du texte
    gsap.from('.hero-title', {
      duration: 1.5,
      y: 100,
      opacity: 0,
      ease: 'power4.out'
    });

    gsap.from('.hero-text', {
      duration: 1.5,
      y: 50,
      opacity: 0,
      delay: 0.5,
      ease: 'power4.out'
    });
  }
}
</script>
<style>
.hero-section {
  min-height: 100vh;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  padding: 2rem;
}

.particles-container {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}

.particle {
  position: absolute;
  width: 6px;
  height: 6px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
}

.hero-content {
  max-width: 1400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  opacity: 0;
  transform: translateY(30px);
  transition: all 1s cubic-bezier(0.4, 0, 0.2, 1);
}

.hero-content.visible {
  opacity: 1;
  transform: translateY(0);
}

.hero-text-container {
  color: white;
  z-index: 2;
}

.hero-title {
  font-size: 4rem;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 2rem;
  background: linear-gradient(to right, #fff, #64ffda);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  text-shadow: 0 0 20px rgba(100, 255, 218, 0.3);
}

.hero-text {
  font-size: 1.25rem;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: 3rem;
}

.button-container {
  display: flex;
  gap: 1.5rem;
}

.cta-button {
  padding: 1rem 2rem;
  border-radius: 30px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.cta-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
  transform: translateX(-100%);
  transition: 0.5s;
}

.cta-button:hover::before {
  transform: translateX(100%);
}

.primary {
  background: linear-gradient(45deg, #64ffda, #0891b2);
  border: none;
  color: white;
}

.secondary {
  background: transparent;
  border: 2px solid #64ffda;
  color: #64ffda;
}

.hero-visual {
  position: relative;
  height: 100%;
}

.geometric-shape {
  width: 400px;
  height: 400px;
  background: linear-gradient(45deg, rgba(100, 255, 218, 0.1), rgba(8, 145, 178, 0.1));
  border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  position: absolute;
  animation: morphShape 8s ease-in-out infinite;
}

.floating-elements {
  position: absolute;
  width: 100%;
  height: 100%;
}

.float-item {
  position: absolute;
  width: 20px;
  height: 20px;
  background: rgba(100, 255, 218, 0.2);
  border-radius: 50%;
  animation: float 4s ease-in-out infinite;
}


@keyframes morphShape {
  0% {
    border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  }
  50% {
    border-radius: 30% 60% 70% 40% / 50% 60% 30% 60%;
  }
  100% {
    border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  }
}




@keyframes float {
  0% { transform: translateY(0) rotate(0deg); }
  50% { transform: translateY(-20px) rotate(180deg); }
  100% { transform: translateY(0) rotate(360deg); }
}

@media (max-width: 1024px) {
  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .hero-title {
    font-size: 3rem;
  }

  .button-container {
    justify-content: center;
  }

  .hero-visual {
    display: none;
  }
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }

  .hero-text {
    font-size: 1.1rem;
  }

  .button-container {
    flex-direction: column;
  }

  .cta-button {
    width: 100%;
  }
}
</style>