<template>
  <section class="process-section" id="pa">
    <div class="container">
      <span class="section-subtitle">Our Process</span>
      
      <div class="process-header">
        <div class="process-title">
          <h2>Notre processus de travail vous aide à tirer le meilleur parti des compétences de notre équipe</h2>
        </div>
        <div class="process-description">
          <p>Avec la connaissance de notre équipe de différents processus, nous choisissons le processus parfait pour s'adapter au développement de votre produit</p>
        </div>
      </div>

      <div class="process-steps">
        <div class="process-card" v-for="(step, index) in steps" :key="index">
          <div class="step-header">
            <span class="step-number">{{ String(index + 1).padStart(2, '0') }}</span>
            <h3 class="step-title">{{ step.title }}</h3>
          </div>
          <p class="step-description">{{ step.description }}</p>
          <div class="step-indicator"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const steps = [
  {
    title: 'Recherche',
    description: 'User research helps us find out exactly how our target customers feel when interacting with a product'
  },
  {
    title: 'Designer',
    description: 'User research helps us find out exactly how our target customers feel when interacting with a product'
  },
  {
    title: 'Développement',
    description: 'User research helps us find out exactly how our target customers feel when interacting with a product'
  },
  {
    title: 'Test',
    description: 'User research helps us find out exactly how our target customers feel when interacting with a product'
  }
]
</script>

<style scoped>
.process-section {
  padding: 8rem 0;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
  min-height: 100vh;
  display: flex;
  align-items: center;
  color: white;
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
}

.section-subtitle {
  display: inline-block;
  font-size: 1.1rem;
  font-weight: 600;
  color: #64ffda;
  margin-bottom: 1.5rem;
  padding: 0.5rem 1rem;
  background: rgba(100, 255, 218, 0.1);
  border-radius: 30px;
}

.process-header {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  margin-bottom: 6rem;
}

.process-title h2 {
  font-size: 2.5rem;
  font-weight: 700;
  line-height: 1.3;
  background: linear-gradient(to right, #fff, #64ffda);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.process-description p {
  font-size: 1.25rem;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.8);
}

.process-steps {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2rem;
}

.process-card {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 20px;
  padding: 2rem;
  position: relative;
  transition: all 0.3s ease;
}

.process-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.1);
}

.step-header {
  margin-bottom: 1.5rem;
}

.step-number {
  font-size: 3rem;
  font-weight: 700;
  background: linear-gradient(45deg, #64ffda, #0891b2);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  display: block;
  margin-bottom: 1rem;
}

.step-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #64ffda;
  margin-bottom: 1rem;
}

.step-description {
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.6;
}

.step-indicator {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 3px;
  background: linear-gradient(45deg, #64ffda, #0891b2);
  transition: width 0.3s ease;
}

.process-card:hover .step-indicator {
  width: 100%;
}

@media (max-width: 1200px) {
  .process-steps {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .process-section {
    padding: 4rem 0;
  }

  .container {
    padding: 0 1.5rem;
  }

  .process-header {
    grid-template-columns: 1fr;
    gap: 2rem;
    margin-bottom: 3rem;
  }

  .process-title h2 {
    font-size: 2rem;
  }

  .process-description p {
    font-size: 1.1rem;
  }

  .process-steps {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}

@media (max-width: 480px) {
  .process-title h2 {
    font-size: 1.75rem;
  }

  .process-card {
    padding: 1.5rem;
  }

  .step-number {
    font-size: 2.5rem;
  }

  .step-title {
    font-size: 1.25rem;
  }
}
</style>