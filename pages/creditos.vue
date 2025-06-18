<template>
  <div class="sports-content-container">
    <!-- Menú lateral fijo -->
    <aside class="sidebar-menu">
      <div class="sidebar-header">
        <h3 class="sidebar-title">MENÚ</h3>
      </div>
      <nav class="sidebar-nav">
        <NuxtLink
          v-for="option in menuOptions"
          :key="option.id"
          :to="option.route"
          class="sidebar-option"
          :class="{ active: currentPage === option.id }"
          @click="navigateToPage(option.id)"
        >
          <div class="sidebar-icon">{{ option.icon }}</div>
          <span class="sidebar-text">{{ option.title }}</span>
        </NuxtLink>
      </nav>
    </aside>

    <!-- Contenido principal -->
    <div class="main-content">
      <!-- Header -->
      <header class="sports-header">
        <div class="header-content">
          <button class="back-btn" @click="goBack">
            <span class="back-arrow">←</span>
            VOLVER
          </button>
          <h1 class="main-title">
            <span class="title-icon">🏀</span>
            CREDITOS
            <span class="title-icon">🏀</span>
          </h1>
        </div>
        <div class="header-decoration"></div>
      </header>

      <!-- Contenido principal -->
      <main class="content-grid">
        <!-- Sección de jugadores -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">🏀 PARTICIPANTES</h2>
          </div>
          <div class="card-content">
            <div class="players-grid">
              <div class="player-item">
                <img
                  src="/imagenes/participantes/Alejandra.jpg"
                  alt="Alejandra"
                  class="player-image"
                  @error="handleImageError"
                >
                <h3 class="player-name">Alejandra Perez</h3>
              </div>
              <div class="player-item">
                <img
                  src="/imagenes/participantes/Juliana.jpg"
                  alt="Juliana"
                  class="player-image"
                  @error="handleImageError"
                >
                <h3 class="player-name">Juliana Ripoll</h3>
              </div>
              <div class="player-item">
                <img
                  src="/imagenes/participantes/steven.jpg"
                  alt="Steven"
                  class="player-image"
                  @error="handleImageError"
                >
                <h3 class="player-name">Steven Morales</h3>
              </div>
              <div class="player-item">
                <img
                  src="/imagenes/participantes/Yo.jpg"
                  alt="Yo"
                  class="player-image"
                  @error="handleImageError"
                >
                <h3 class="player-name">Diego Gutierrez</h3>
              </div>
            </div>
          </div>
        </section>

        <!-- Portada académica -->
        <section class="content-card full-width cover-section">
          <div class="cover-container">
            <div class="cover-decoration top"></div>
            <div class="cover-content">
              <img
                src="https://www.unicordoba.edu.co/wp-content/uploads/2025/04/Escudo-unicordoba-2025.png"
                alt="Universidad de Córdoba Logo"
                class="university-logo"
              >
              <h2 class="cover-title">
                LICENCIATURA EN INFORMÁTICA
                <span class="emphasis-line">CON ÉNFASIS EN MEDIOS AUDIOVISUALES</span>
              </h2>
              <div class="cover-divider"></div>
              <div class="year-display">
                <span class="year-number">2025</span>
              </div>
              <div class="academic-details">
                <div class="detail-item">
                  <span class="detail-icon">📚</span>
                  <span class="detail-text">PROYECTO ACADÉMICO</span>
                </div>
                <div class="detail-item">
                  <span class="detail-icon">🎯</span>
                  <span class="detail-text">MEDIOS DIGITALES</span>
                </div>
                <div class="detail-item">
                  <span class="detail-icon">💻</span>
                  <span class="detail-text">TECNOLOGÍA EDUCATIVA</span>
                </div>
              </div>
            </div>
            <div class="cover-decoration bottom"></div>
          </div>
        </section>
      </main>
    </div>

    <!-- Fondo decorativo -->
    <div class="background-elements">
      <div class="bg-circle circle-1"></div>
      <div class="bg-circle circle-2"></div>
      <div class="bg-circle circle-3"></div>
      <div class="basketball-texture"></div>
    </div>

    <!-- Líneas de cancha -->
    <div class="court-lines">
      <div class="line1"></div>
      <div class="line2"></div>
      <div class="circle1"></div>
      <div class="circle2"></div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter, useRoute } from 'nuxt/app'

const router = useRouter()
const route = useRoute()
const currentPage = ref(1) // ID de la página actual, inicializado a CONTENIDO

// Opciones del menú lateral
const menuOptions = ref([
  { id: 1, icon: '📚', title: 'CONTENIDO', route: '/contenido' },
  { id: 2, icon: '🏀', title: 'GUIAS', route: '/guias' },
  { id: 3, icon: '🏃‍♂️', title: 'ACTIVIDADES', route: '/actividades' },
  { id: 4, icon: '📋', title: 'EVALUACION', route: '/evaluacion' },
  { id: 5, icon: '🎖️', title: 'CREDITOS', route: '/creditos' }
])

// Actualizar currentPage según la ruta actual al montar el componente
onMounted(() => {
  const currentRoute = route.path
  const matchedOption = menuOptions.value.find(opt => opt.route === currentRoute)
  if (matchedOption) {
    currentPage.value = matchedOption.id
  }
})

function goBack() {
  router.push('/')
}

function navigateToPage(optionId) {
  const option = menuOptions.value.find(opt => opt.id === optionId)
  if (option?.route) {
    currentPage.value = optionId
    // Navigation handled by NuxtLink
  }
}

// Función para manejar errores de carga de imágenes
function handleImageError(event) {
  event.target.src = 'https://via.placeholder.com/300x300/ff8c00/ffffff?text=Jugador'
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Roboto:wght@400;700;900&display=swap');

.sports-content-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 50%, #0f1419 100%);
  position: relative;
  overflow: hidden;
  font-family: 'Roboto', sans-serif;
  display: flex;
}

/* Menú lateral fijo */
.sidebar-menu {
  position: fixed;
  left: 0;
  top: 0;
  width: 280px;
  height: 100vh;
  background: linear-gradient(180deg, rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.7));
  backdrop-filter: blur(20px);
  border-right: 2px solid rgba(255, 140, 0, 0.3);
  z-index: 1000;
  display: flex;
  flex-direction: column;
  box-shadow: 5px 0 20px rgba(0, 0, 0, 0.5);
}

.sidebar-header {
  padding: 2rem 1.5rem;
  border-bottom: 2px solid rgba(255, 140, 0, 0.3);
  background: linear-gradient(145deg, rgba(255, 140, 0, 0.1), rgba(255, 140, 0, 0.05));
}

.sidebar-title {
  font-family: 'Bebas Neue', cursive;
  font-size: 1.8rem;
  color: #ff8c00;
  text-align: center;
  margin: 0;
  letter-spacing: 3px;
  text-shadow: 0 0 15px rgba(255, 140, 0, 0.5);
}

.sidebar-nav {
  flex: 1;
  padding: 2rem 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.sidebar-option {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem 1.5rem;
  margin: 0 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  border-radius: 12px;
  color: rgba(255, 255, 255, 0.8);
  border: 1px solid transparent;
  text-decoration: none;
}

.sidebar-option:hover {
  background: linear-gradient(145deg, rgba(255, 140, 0, 0.2), rgba(255, 140, 0, 0.1));
  border-color: rgba(255, 140, 0, 0.4);
  color: #ffffff;
  transform: translateX(5px);
}

.sidebar-option.active {
  background: linear-gradient(145deg, rgba(255, 140, 0, 0.3), rgba(255, 140, 0, 0.15));
  border-color: #ff8c00;
  color: #ffffff;
  box-shadow: 0 5px 15px rgba(255, 140, 0, 0.3);
}

.sidebar-icon {
  font-size: 1.5rem;
  filter: drop-shadow(0 0 10px rgba(255, 140, 0, 0.5));
}

.sidebar-text {
  font-family: 'Bebas Neue', cursive;
  font-size: 1.1rem;
  letter-spacing: 1px;
}

/* Contenido principal */
.main-content {
  margin-left: 280px;
  width: calc(100% - 280px);
  position: relative;
  z-index: 10;
}

/* Elementos de fondo */
.background-elements {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  pointer-events: none;
}

.bg-circle {
  position: absolute;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255, 140, 0, 0.1), transparent);
  animation: float 8s ease-in-out infinite;
}

.circle-1 {
  width: 250px;
  height: 250px;
  top: 15%;
  right: -125px;
  animation-delay: 0s;
}

.circle-2 {
  width: 180px;
  height: 180px;
  bottom: 20%;
  left: -90px;
  animation-delay: 3s;
}

.circle-3 {
  width: 120px;
  height: 120px;
  top: 60%;
  left: 80%;
  background: radial-gradient(circle, rgba(255, 69, 0, 0.15), transparent);
  animation-delay: 6s;
}

.basketball-texture {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    radial-gradient(circle at 20% 50%, rgba(255, 140, 0, 0.03) 2px, transparent 2px),
    radial-gradient(circle at 80% 50%, rgba(255, 140, 0, 0.03) 2px, transparent 2px);
  background-size: 50px 50px;
  animation: texture-move 20s linear infinite;
}

/* Líneas de cancha */
.court-lines {
  position: absolute;
  top: 0;
  left: 280px;
  width: calc(100% - 280px);
  height: 100%;
  z-index: 2;
  pointer-events: none;
  opacity: 0.15;
}

.line1 {
  position: absolute;
  background: #ff8c00;
  box-shadow: 0 0 10px rgba(255, 140, 0, 0.3);
  top: 50%;
  left: 0;
  width: 100%;
  height: 3px;
  transform: translateY(-50%);
}

.line2 {
  position: absolute;
  bottom: 20%;
  left: 50%;
  width: 300px;
  height: 150px;
  border: 3px solid #ff8c00;
  border-bottom: none;
  border-radius: 150px 150px 0 0;
  background: none;
  transform: translateX(-50%);
  box-shadow: 0 0 10px rgba(255, 140, 0, 0.3);
}

.circle1 {
  position: absolute;
  border: 3px solid #ff8c00;
  border-radius: 50%;
  background: none;
  box-shadow: 0 0 10px rgba(255, 140, 0, 0.3);
  top: 50%;
  left: 50%;
  width: 120px;
  height: 120px;
  transform: translate(-50%, -50%);
}

.circle2 {
  position: absolute;
  border: 3px solid #ff8c00;
  border-radius: 50%;
  background: none;
  box-shadow: 0 0 10px rgba(255, 140, 0, 0.3);
  bottom: 25%;
  left: 50%;
  width: 80px;
  height: 80px;
  transform: translateX(-50%);
}

/* Header */
.sports-header {
  text-align: center;
  padding: 3rem 2rem 2rem;
  position: relative;
  z-index: 10;
}

.header-content {
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  backdrop-filter: blur(15px);
  border: 2px solid rgba(255, 140, 0, 0.3);
  border-radius: 20px;
  padding: 2rem;
  box-shadow: 0 15px 35px rgba(255, 140, 0, 0.4);
  position: relative;
}

.back-btn {
  position: absolute;
  top: 1rem;
  left: 1rem;
  background: linear-gradient(145deg, rgba(255, 140, 0, 0.2), rgba(255, 140, 0, 0.1));
  border: 1px solid rgba(255, 140, 0, 0.4);
  border-radius: 25px;
  color: #ffffff;
  padding: 0.5rem 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  font-family: 'Roboto', sans-serif;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.back-btn:hover {
  background: linear-gradient(145deg, rgba(255, 140, 0, 0.4), rgba(255, 140, 0, 0.2));
  border-color: #ff8c00;
  transform: translateX(-5px);
  box-shadow: 0 5px 15px rgba(255, 140, 0, 0.3);
}

.back-arrow {
  font-size: 1.2rem;
  transition: transform 0.3s ease;
}

.back-btn:hover .back-arrow {
  transform: translateX(-3px);
}

.main-title {
  font-family: 'Bebas Neue', cursive;
  font-size: clamp(2rem, 4vw, 2.8rem);
  font-weight: 400;
  color: #ff8c00;
  text-shadow: 0 0 20px rgba(255, 140, 0, 0.5);
  margin: 0;
  letter-spacing: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.title-icon {
  color: #ffd700;
  text-shadow: 0 0 15px rgba(255, 215, 0, 0.7);
  font-size: 2.2rem;
}

.header-decoration {
  height: 4px;
  background: linear-gradient(90deg, transparent, #ff8c00, #ffd700, #ff8c00, transparent);
  margin-top: 1rem;
  border-radius: 2px;
  box-shadow: 0 0 10px rgba(255, 140, 0, 0.5);
}

/* Contenido */
.content-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  padding: 2rem;
  max-width: 1400px;
  margin: 0 auto;
  position: relative;
  z-index: 10;
}

.content-card {
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  backdrop-filter: blur(15px);
  border-radius: 20px;
  border: 2px solid rgba(255, 140, 0, 0.3);
  overflow: hidden;
  transition: all 0.3s ease;
  box-shadow: 0 8px 25px rgba(255, 140, 0, 0.2);
}

.content-card:hover {
  border-color: #ff8c00;
  box-shadow: 0 15px 35px rgba(255, 140, 0, 0.4);
  transform: translateY(-5px);
}

.full-width {
  grid-column: 1 / -1;
}

.card-header {
  background: linear-gradient(135deg, rgba(255, 140, 0, 0.3), rgba(255, 140, 0, 0.1));
  padding: 1.5rem;
  border-bottom: 1px solid rgba(255, 140, 0, 0.3);
}

.card-title {
  color: #ffffff;
  font-family: 'Bebas Neue', cursive;
  font-size: 1.5rem;
  font-weight: 400;
  margin: 0;
  letter-spacing: 2px;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
}

.card-content {
  padding: 2rem;
}

/* Jugadores */
.players-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.player-item {
  text-align: center;
}

.player-image {
  width: 200px;
  height: 200px;
  object-fit: cover;
  border-radius: 10px;
  border: 2px solid rgba(255, 140, 0, 0.3);
  box-shadow: 0 5px 15px rgba(255, 140, 0, 0.2);
  transition: all 0.3s ease;
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.player-image:hover {
  border-color: #ff8c00;
  box-shadow: 0 10px 25px rgba(255, 140, 0, 0.4);
  transform: translateY(-5px);
}

.player-name {
  color: #ff8c00;
  font-family: 'Bebas Neue', cursive;
  font-size: 1.3rem;
  margin-top: 1rem;
  text-shadow: 0 0 10px rgba(255, 140, 0, 0.5);
  width: 200px; /* Matches player-image width */
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}

/* Portada académica */
.cover-section {
  margin-top: 2rem;
  background: linear-gradient(145deg, rgba(255, 215, 0, 0.1), rgba(255, 140, 0, 0.05));
  border: 3px solid rgba(255, 215, 0, 0.4);
}

.cover-container {
  position: relative;
  padding: 0;
  min-height: 400px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.cover-decoration {
  position: absolute;
  left: 0;
  right: 0;
  height: 6px;
  background: linear-gradient(90deg, 
    transparent, 
    rgba(255, 215, 0, 0.8), 
    rgba(255, 140, 0, 0.8), 
    rgba(255, 215, 0, 0.8), 
    transparent
  );
  box-shadow: 0 0 20px rgba(255, 215, 0, 0.6);
}

.cover-decoration.top {
  top: 0;
  border-radius: 20px 20px 0 0;
}

.cover-decoration.bottom {
  bottom: 0;
  border-radius: 0 0 20px 20px;
}

.cover-content {
  text-align: center;
  padding: 3rem 2rem;
  z-index: 10;
  position: relative;
}

.university-logo {
  height: clamp(2rem, 4vw, 3.5rem); /* Matches cover-title font-size */
  width: auto;
  margin-bottom: 1.5rem;
  margin-left: auto;
  margin-right: auto;
  display: block; /* Ensures centering works */
  filter: drop-shadow(0 0 20px rgba(255, 215, 0, 0.8));
  animation: pulse 3s ease-in-out infinite;
}

.cover-title {
  font-family: 'Bebas Neue', cursive;
  font-size: clamp(2rem, 4vw, 3.5rem);
  color: #ffd700;
  text-shadow: 
    0 0 10px rgba(255, 215, 0, 0.5),
    婚 0 20px rgba(255, 215, 0, 0.3),
    0 0 30px rgba(255, 215, 0, 0.2);
  margin: 0 0 1rem 0;
  letter-spacing: 3px;
  line-height: 1.2;
}

.emphasis-line {
  display: block;
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  color: #ff8c00;
  margin-top: 0.5rem;
  text-shadow: 
    0 0 10px rgba(255, 140, 0, 0.5),
    0 0 20px rgba(255, 140, 0, 0.3);
}

.cover-divider {
  width: 200px;
  height: 3px;
  background: linear-gradient(90deg, transparent, #ffd700, #ff8c00, #ffd700, transparent);
  margin: 2rem auto;
  border-radius: 2px;
  box-shadow: 0 0 15px rgba(255, 215, 0, 0.5);
}

.year-display {
  margin: 2rem 0;
}

.year-number {
  font-family: 'Bebas Neue', cursive;
  font-size: clamp(2rem, 4vw, 3rem); /* Reduced size */
  color: #ffffff;
  text-shadow: 
    0 0 15px rgba(255, 255, 255, 0.5),
    0 0 30px rgba(255, 215, 0, 0.3);
  font-weight: 900;
  letter-spacing: 6px;
  display: inline-block;
  padding: 0.5rem 1rem; /* Reduced padding */
  border: 2px solid rgba(255, 215, 0, 0.5); /* Thinner border */
  border-radius: 10px; /* Smaller border-radius */
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  backdrop-filter: blur(10px);
}

.academic-details {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 2rem;
  margin-top: 3rem;
}

.detail-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem;
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  border: 1px solid rgba(255, 215, 0, 0.3);
  border-radius: 12px;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
}

.detail-item:hover {
  border-color: #ffd700;
  box-shadow: 0 10px 25px rgba(255, 215, 0, 0.3);
  transform: translateY(-5px);
}

.detail-icon {
  font-size: 2rem;
  filter: drop-shadow(0 0 10px rgba(255, 215, 0, 0.5));
}

.detail-text {
  font-family: 'Bebas Neue', cursive;
  font-size: 0.9rem;
  color: #ffffff;
  letter-spacing: 1px;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
}

/* Animaciones */
@keyframes float {
  0%, 100% {
    transform: translateY( 0px) rotate(0deg);
  }
  50% {
    transform: translateY(-15px) rotate(5deg);
  }
}

@keyframes texture-move {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(50px);
  }
}

@keyframes pulse {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
}

/* Responsive */
@media (max-width: 1024px) {
  .sidebar-menu {
    width: 240px;
  }
  
  .main-content {
    margin-left: 240px;
    width: calc(100% - 240px);
  }
  
  .court-lines {
    left: 240px;
    width: calc(100% - 240px);
  }
}

@media (max-width: 768px) {
  .sidebar-menu {
    transform: translateX(-100%);
    transition: transform 0.3s ease;
  }
  
  .sidebar-menu.open {
    transform: translateX(0);
  }
  
  .main-content {
    margin-left: 0;
    width: 100%;
  }
  
  .court-lines {
    left: 0;
    width: 100%;
  }
  
  .content-grid {
    grid-template-columns: 1fr;
    padding: 1rem;
  }
  
  .main-title {
    font-size: 2rem;
  }
  
  .back-btn {
    position: relative;
    margin-bottom: 1rem;
  }
  
  .academic-details {
    flex-direction: column;
    align-items: center;
  }
  
  .detail-item {
    width: 100%;
    max-width: 300px;
  }
}

@media (max-width: 480px) {
  .sports-header {
    padding: 2rem 1rem 1rem;
  }
  
  .header-content {
    padding: 1.5rem;
  }
  
  .main-title {
    font-size: 1.8rem;
    letter-spacing: 1px;
  }
  
  .title-icon {
    margin: 0 0.5rem;
    font-size: 1.8rem;
  }
  
  .card-content {
    padding: 1.5rem;
  }
  
  .sidebar-text {
    font-size: 0.9rem;
  }
  
  .cover-content {
    padding: 2rem 1rem;
  }
  
  .year-number {
    padding: 0.5rem 1rem;
    letter-spacing: 4px;
  }
  
  .university-logo {
    height: clamp(1.8rem, 3.5vw, 3rem); /* Adjusted for smaller screens */
  }
  
  .player-image,
  .player-name {
    width: 150px; /* Adjust for smaller screens */
  }
}
</style>