<template>
  <div class="sports-content-container">
    <!-- Menú lateral fijo -->
    <aside class="sidebar-menu">
      <div class="sidebar-header">
        <h3 class="sidebar-title">MENÚ</h3>
      </div>
      <nav class="sidebar-nav">
        <div 
          v-for="option in menuOptions" 
          :key="option.id"
          class="sidebar-option" 
          @click="navigateToPage(option.id)"
          :class="{ active: currentPage === option.id }"
        >
          <div class="sidebar-icon">{{ option.icon }}</div>
          <span class="sidebar-text">{{ option.title }}</span>
        </div>
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
            ACTIVIDADES DE BALONCESTO
            <span class="title-icon">🏀</span>
          </h1>
          <p class="subtitle">Practica y aprende con estas actividades interactivas</p>
        </div>
        <div class="header-decoration"></div>
      </header>

      <!-- Contenido principal -->
      <main class="content-grid">
        <!-- Sección de actividad -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">🏃‍♂️ {{ currentActivity.title }}</h2>
          </div>
          <div class="card-content">
            <div class="activity-content">
              <iframe 
                :src="currentActivity.iframeUrl" 
                class="activity-iframe"
                :allow="currentActivity.allow"
                allowfullscreen
                frameborder="0"
                :title="currentActivity.title"
              ></iframe>
            </div>
            <!-- Menú de navegación de actividades -->
            <nav class="activity-nav">
              <button 
                v-for="(activity, index) in activities" 
                :key="index"
                class="activity-nav-item"
                :class="{ 'active-nav-item': currentActivityIndex === index }"
                @click="selectActivity(index)"
              >
                {{ activity.title }}
              </button>
            </nav>
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
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const currentPage = ref(3) // ID de la página actual (ACTIVIDADES)

// Lista de actividades
const activities = ref([
  {
    title: 'Historia del Baloncesto',
    iframeUrl: 'https://www.educaplay.com/game/24307663-historia_del_baloncesto.html',
    allow: 'fullscreen; autoplay; allow-top-navigation-by-user-activation'
  },
  {
    title: 'Completa los Espacios en Blanco',
    iframeUrl: 'https://es.educaplay.com/juego/24308141-completa_los_espacios_en_blanco_sobre_el_baloncesto.html',
    allow: 'fullscreen; autoplay; allow-top-navigation-by-user-activation'
  },
  {
    title: 'Cuestionario de Baloncesto',
    iframeUrl: 'https://wordwall.net/es/embed/7018eab803ca4ec7ba60ea845b0677fb?themeId=56&templateId=30&fontStackId=0',
    allow: 'fullscreen'
  }
])

// Estado para la actividad actual
const currentActivityIndex = ref(0)
const currentActivity = computed(() => activities.value[currentActivityIndex.value])

// Función para cambiar de actividad
function selectActivity(index) {
  currentActivityIndex.value = index
}

function goBack() {
  console.log('Attempting to navigate to main menu: /') // Debug: Log intento
  router.push('/').then(() => {
    console.log('Navigation successful to main menu: /') // Debug: Éxito
  }).catch(error => {
    console.error('Navigation failed to main menu: /', 'Error:', error) // Debug: Fallo
    alert(`No se pudo navegar al menú principal. Verifica que la página exista. Error: ${error.message}`)
  })
}

async function navigateToPage(optionId) {
  console.log('Navigating to option:', optionId) // Debug log
  const option = menuOptions.value.find(opt => opt.id === optionId)
  if (option?.route) {
    try {
      currentPage.value = optionId // Update currentPage before navigation
      await router.push(option.route)
      console.log('Navigation successful to:', option.route) // Debug log
    } catch (error) {
      console.error('Navigation error:', error)
      // Optionally, reset currentPage if navigation fails
      currentPage.value = 3 // Revert to ACTIVIDADES
    }
  } else {
    console.warn('No route found for option:', optionId) // Debug log
  }
}

const menuOptions = ref([
  { id: 1, icon: '📚', title: 'CONTENIDO', route: '/contenido' },
  { id: 2, icon: '🏀', title: 'GUIAS', route: '/guias' },
  { id: 3, icon: '🏃‍♂️', title: 'ACTIVIDADES', route: '/actividades' },
  { id: 4, icon: '📋', title: 'EVALUACION', route: '/evaluacion' },
  { id: 5, icon: '🎖️', title: 'CREDITOS', route: '/creditos' }
])
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

.subtitle {
  color: rgba(255, 255, 255, 0.9);
  font-size: clamp(0.9rem, 2vw, 1.1rem);
  margin: 1rem 0 0;
  opacity: 0.9;
  font-weight: 400;
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
  grid-template-columns: 1fr;
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
  padding: 2.5rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.activity-content {
  width: 100%;
  text-align: center;
}

.activity-iframe {
  width: 100%;
  max-width: 100%;
  height: calc(100vh - 220px);
  max-height: 750px;
  min-height: 450px;
  border: 1px solid rgba(255, 140, 0, 0.3);
  border-radius: 8px;
  box-shadow: 0 5px 15px rgba(255, 140, 0, 0.2);
}

/* Menú de navegación de actividades */
.activity-nav {
  display: flex;
  gap: 0.8rem;
  margin-top: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}

.activity-nav-item {
  background: linear-gradient(135deg, rgba(255, 140, 0, 0.2), rgba(255, 140, 0, 0.1));
  color: #ffffff;
  padding: 0.4rem 0.8rem;
  border-radius: 8px;
  border: 1px solid rgba(255, 140, 0, 0.4);
  font-family: 'Bebas Neue', cursive;
  font-size: 0.9rem;
  letter-spacing: 1px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.activity-nav-item:hover {
  background: linear-gradient(135deg, rgba(255, 140, 0, 0.4), rgba(255, 140, 0, 0.2));
  border-color: #ff8c00;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(255, 140, 0, 0.3);
}

.active-nav-item {
  background: linear-gradient(135deg, #ff8c00, #ffd700);
  border-color: #ffd700;
  color: #ffffff;
  box-shadow: 0 5px 15px rgba(255, 140, 0, 0.4);
}

/* Animaciones */
@keyframes float {
  0%, 100% {
    transform: translateY(0px) rotate(0deg);
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

  .activity-iframe {
    height: calc(100vh - 200px);
    max-height: 650px;
    min-height: 400px;
  }

  .card-content {
    padding: 2rem;
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
    padding: 1rem;
  }
  
  .main-title {
    font-size: 2rem;
  }
  
  .back-btn {
    position: relative;
    margin-bottom: 1rem;
  }

  .activity-iframe {
    height: calc(100vh - 180px);
    max-height: 550px;
    min-height: 350px;
  }

  .activity-nav-item {
    font-size: 0.8rem;
    padding: 0.3rem 0.6rem;
  }

  .card-content {
    padding: 1.5rem;
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
    padding: 1rem;
  }
  
  .sidebar-text {
    font-size: 0.9rem;
  }

  .activity-iframe {
    height: calc(100vh - 160px);
    max-height: 450px;
    min-height: 300px;
  }

  .activity-nav-item {
    font-size: 0.7rem;
    padding: 0.2rem 0.5rem;
  }
}
</style>