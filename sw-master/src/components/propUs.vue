<template>
  <section class="about-section" id="page">
    <div class="container">
      <div class="about-content">
        <span class="section-subtitle">À propos de nous</span>
        <h2 class="section-title">Au cœur de notre succès se trouve notre équipe pluridisciplinaire</h2>
        
        <div class="about-description">
          <p>YUCCAINFO est un partenaire stratégique pour la transformation numérique des entreprises, alliant technologie de pointe, créativité et vision d’avenir. L'entreprise offre des solutions innovantes, fiables, évolutives et centrées sur le client, visant à accompagner les entreprises dans leur digitalisation et à transformer leurs idées en réussites concrètes. YUCCAINFO contribue à la modernisation des entreprises tunisiennes et internationales à travers des solutions technologiques intelligentes et des projets sur mesure.</p>
        </div>

        <div class="button-group">
          <button class="primary-button">
            <span>Parlons</span>
            <img src="../assets/messagee.png" alt="Message icon" class="button-icon">
          </button>
          
          <button class="secondary-button">
            <span>Check our services</span>
            <img src="../assets/flesh1.png" alt="Arrow icon" class="button-icon">
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Component logic here if needed
</script>

<style scoped>
.about-section {
  padding: 8rem 0;
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

.about-content {
  max-width: 900px;
  margin: 0 auto;
  text-align: center;
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

.section-title {
  font-size: 3rem;
  font-weight: 700;
  line-height: 1.3;
  margin-bottom: 2rem;
  background: linear-gradient(45deg, #1a1a2e, #0f3460);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.about-description {
  margin-bottom: 3rem;
}

.about-description p {
  font-size: 1.25rem;
  line-height: 1.8;
  color: #666;
}

.button-group {
  display: flex;
  gap: 2rem;
  justify-content: center;
  align-items: center;
}

.primary-button, .secondary-button {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem 2rem;
  border-radius: 30px;
  font-weight: 600;
  font-size: 1.1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.primary-button {
  background: linear-gradient(45deg, #1a1a2e, #0f3460);
  color: white;
  border: none;
}

.primary-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(26, 26, 46, 0.2);
}

.secondary-button {
  background: transparent;
  color: #1a1a2e;
  border: none;
  position: relative;
}

.secondary-button::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background: #1a1a2e;
  transition: width 0.3s ease;
}

.secondary-button:hover::after {
  width: 100%;
}

.button-icon {
  width: 20px;
  height: 20px;
  object-fit: contain;
}

@media (max-width: 768px) {
  .about-section {
    padding: 6rem 0;
  }

  .container {
    padding: 0 1.5rem;
  }

  .section-title {
    font-size: 2.25rem;
  }

  .about-description p {
    font-size: 1.1rem;
  }

  .button-group {
    flex-direction: column;
    gap: 1rem;
  }

  .primary-button, .secondary-button {
    width: 100%;
    justify-content: center;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 1.75rem;
  }

  .about-description p {
    font-size: 1rem;
  }
}
</style>