<template>
  <section class="services-section" id="toteee">
    <div class="container">
      <h2 class="section-title">Nos Services</h2>
      
      <div class="services-container" v-if="screenWidth > 768">
        <div class="services-nav">
          <div 
            v-for="(content, title) in servicesData" 
            :key="title"
            class="service-nav-item"
            :class="{ active: selectedTitle === title }"
            @click="selectTitle(title)"
          >
            <span class="service-nav-text">{{ title }}</span>
          </div>
        </div>

        <div class="service-content" v-if="selectedTitle">
          <div class="service-card" :class="{ visible: isContentVisible }">
            <div class="service-image">
              <img :src="servicesData[selectedTitle].image" :alt="selectedTitle">
            </div>
            <div class="service-description">
              <h3>{{ selectedTitle }}</h3>
              <p>{{ servicesData[selectedTitle].description }}</p>
              <button class="learn-more-btn">En savoir plus</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Mobile Version -->
      <div class="services-accordion" v-else>
        <div 
          v-for="(service, title) in servicesData" 
          :key="title" 
          class="accordion-item"
        >
          <div 
            class="accordion-header"
            :class="{ active: selectedTitle === title }"
            @click="toggleAccordion(title)"
          >
            <span>{{ title }}</span>
            <span class="accordion-icon">+</span>
          </div>
          <div 
            class="accordion-content"
            :class="{ active: selectedTitle === title }"
          >
            <img :src="service.image" :alt="title">
            <p>{{ service.description }}</p>
            <button class="learn-more-btn">En savoir plus</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
  return {
    screenWidth: window.innerWidth,
    selectedTitle: "Ingénierie Logicielle", // Choix initial
    isContentVisible: true,
    servicesData: {
      "Ingénierie Logicielle": {
        image: "https://images.pexels.com/photos/3183150/pexels-photo-3183150.jpeg",
        description: "Développement d’applications web, mobiles et desktop sur mesure, utilisant les technologies les plus récentes comme Laravel, React, Flutter, et plus."
      },
      "Transformation Digitale": {
        image: "https://images.pexels.com/photos/1181467/pexels-photo-1181467.jpeg",
        description: "Accompagnement dans la digitalisation des entreprises avec des solutions ERP sur mesure, systèmes POS performants et une approche cloud-first."
      },
      "Intelligence Artificielle & IoT": {
        image: "https://images.pexels.com/photos/8386440/pexels-photo-8386440.jpeg",
        description: "Exploitation de l’IA et de l’IoT pour offrir des solutions intelligentes, avec des systèmes prédictifs et réactifs grâce à l’apprentissage automatique, la vision par ordinateur et les capteurs connectés."
      },
      "Optimisation SEO & AEO": {
        image: "https://images.pexels.com/photos/1181244/pexels-photo-1181244.jpeg",
        description: "Maximisation de la visibilité en ligne avec des stratégies SEO avancées, optimisation mobile-first, et intégration d’IA pour booster le référencement sur Google, Bing, Siri, Alexa."
      },
      "Cybersécurité & Cloud Computing": {
        image: "https://images.pexels.com/photos/3183150/pexels-photo-3183150.jpeg", // Vous pouvez changer cette image selon les besoins.
        description: "Sécurisation des infrastructures numériques et modernisation par le cloud, avec des solutions de détection d'intrusions, authentification renforcée et hébergement cloud hybride."
      }
    }
  };
},

  methods: {
    selectTitle(title) {
      this.isContentVisible = false;
      setTimeout(() => {
        this.selectedTitle = title;
        this.isContentVisible = true;
      }, 300);
    },
    toggleAccordion(title) {
      this.selectedTitle = this.selectedTitle === title ? '' : title;
    },
    updateScreenWidth() {
      this.screenWidth = window.innerWidth;
    }
  },
  mounted() {
    window.addEventListener('resize', this.updateScreenWidth);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.updateScreenWidth);
  }
};
</script>

<style scoped>
.services-section {
  padding: 6rem 0;
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 4rem;
  background: linear-gradient(45deg, #1a1a2e, #0f3460);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  font-weight: 700;
}

.services-container {
  display: grid;
  grid-template-columns: 300px 1fr;
  gap: 3rem;
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.services-nav {
  background: rgba(26, 26, 46, 0.95);
  padding: 2rem 0;
}

.service-nav-item {
  padding: 1.5rem 2rem;
  color: rgba(255, 255, 255, 0.8);
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
}

.service-nav-item:hover {
  color: #64ffda;
  background: rgba(100, 255, 218, 0.1);
}

.service-nav-item.active {
  color: #64ffda;
  background: rgba(100, 255, 218, 0.1);
}

.service-nav-item.active::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 4px;
  background: #64ffda;
}

.service-content {
  padding: 2rem;
}

.service-card {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.3s ease;
}

.service-card.visible {
  opacity: 1;
  transform: translateY(0);
}

.service-image img {
  width: 100%;
  height: 300px;
  object-fit: cover;
  border-radius: 10px;
  margin-bottom: 2rem;
}

.service-description h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #1a1a2e;
}

.service-description p {
  color: #666;
  line-height: 1.8;
  margin-bottom: 2rem;
}

.learn-more-btn {
  padding: 0.75rem 1.5rem;
  border-radius: 30px;
  background: linear-gradient(45deg, #64ffda, #0891b2);
  border: none;
  color: white;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.learn-more-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(100, 255, 218, 0.2);
}

/* Mobile Accordion Styles */
.services-accordion {
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.accordion-item {
  border-bottom: 1px solid #eee;
}

.accordion-header {
  padding: 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  background: rgba(26, 26, 46, 0.95);
  color: white;
  transition: all 0.3s ease;
}

.accordion-header.active {
  background: linear-gradient(45deg, #1a1a2e, #0f3460);
  color: #64ffda;
}

.accordion-icon {
  font-size: 1.5rem;
  transition: transform 0.3s ease;
}

.accordion-header.active .accordion-icon {
  transform: rotate(45deg);
}

.accordion-content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
}

.accordion-content.active {
  max-height: 300px;
  padding: 1rem;
}

.accordion-content img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 10px;
  margin-bottom: 1.5rem;
}

.accordion-content p {
  color: #666;
  line-height: 1.6;
}
</style>
