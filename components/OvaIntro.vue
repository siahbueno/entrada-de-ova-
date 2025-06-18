<template>
  <div class="basketball-landing-container">
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

    <!-- Elementos flotantes de baloncesto -->
    <div class="floating-elements">
      <div v-for="n in 6" :key="n" 
           class="floating-ball"
           :style="`top: ${Math.random() * 80 + 10}%; left: ${Math.random() * 80 + 10}%; animation-delay: ${n * 0.8}s`">
        🏀
      </div>
    </div>
    
    <Transition name="bounce">
      <div v-if="showContent" class="landing-content">
        <!-- Icono principal -->
        <div class="main-icon-container">
          <div class="main-icon">
            <span class="icon-symbol">🏀</span>
          </div>
        </div>
        
        <!-- Título principal -->
        <h1 class="main-title">
          <span class="title-icon">🏆</span>
          DOMINA LA CANCHA
          <span class="title-icon">🏆</span>
        </h1>
        
        <p class="subtitle">
          Cada tiro es una oportunidad, cada pase una conexión. ¡Salta a la cancha y deja que el baloncesto hable por ti!
        </p>
        
        <!-- Estadísticas de juego -->
        <div class="game-stats">
          <div v-for="(stat, index) in gameStats" :key="index" 
               class="stat-card"
               :style="`animation-delay: ${index * 0.3}s`">
            <div class="stat-number">{{ stat.number }}</div>
            <div class="stat-label">{{ stat.label }}</div>
          </div>
        </div>
        
        <!-- Botón de inicio -->
        <button @click="startExperience" class="start-btn">
          <span>EMPEZAR A JUGAR</span>
          <div class="btn-arrow">🏀</div>
        </button>
      </div>
    </Transition>
  </div>
</template>

<script setup>
// Configuración de Nuxt
definePageMeta({
  layout: false
})

// Composables de Vue
const showContent = ref(false)

// Estadísticas del juego
const gameStats = ref([
  { number: '24', label: 'SEGUNDOS' },
  { number: '3', label: 'PUNTOS' },
  { number: '10', label: 'PIES' },
])

// Lifecycle
onMounted(() => {
  setTimeout(() => {
    showContent.value = true
  }, 500)
})

// Métodos
async function startExperience() {
  // Navegación con Nuxt
  await navigateTo('/menu')
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Roboto:wght@400;700;900&display=swap');

.basketball-landing-container {
  height: 100vh;
  background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 50%, #0f1419 100%);
  position: relative;
  overflow: hidden;
  font-family: 'Roboto', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
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
  left: 0;
  width: 100%;
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

/* Elementos flotantes */
.floating-elements {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 3;
  pointer-events: none;
}

.floating-ball {
  position: absolute;
  font-size: 1.5rem;
  animation: float-basketball 6s ease-in-out infinite;
  opacity: 0.3;
  filter: drop-shadow(0 0 10px rgba(255, 140, 0, 0.5));
}

/* Contenido principal */
.landing-content {
  text-align: center;
  max-width: 700px;
  padding: 1rem;
  position: relative;
  z-index: 10;
}

.main-icon-container {
  margin-bottom: 1.5rem;
}

.main-icon {
  width: 90px;
  height: 90px;
  border-radius: 50%;
  background: linear-gradient(145deg, rgba(255, 140, 0, 0.3), rgba(255, 69, 0, 0.2));
  backdrop-filter: blur(15px);
  border: 3px solid rgba(255, 140, 0, 0.6);
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
  box-shadow: 0 15px 35px rgba(255, 140, 0, 0.4);
  animation: basketball-bounce 2s ease-in-out infinite;
}

.icon-symbol {
  font-size: 2.5rem;
  filter: drop-shadow(0 0 20px rgba(255, 140, 0, 0.8));
}

.main-title {
  font-family: 'Bebas Neue', cursive;
  font-size: 2.8rem;
  font-weight: 400;
  color: #ff8c00;
  text-shadow: 0 0 20px rgba(255, 140, 0, 0.5);
  margin: 0 0 1rem;
  letter-spacing: 4px;
  line-height: 1.1;
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
  font-size: 1.1rem;
  margin: 0 0 2rem;
  line-height: 1.4;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
  font-weight: 400;
}

/* Estadísticas del juego */
.game-stats {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin: 2rem 0;
  flex-wrap: wrap;
}

.stat-card {
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 140, 0, 0.3);
  border-radius: 15px;
  padding: 1rem 1.5rem;
  width: 100px;
  height: 80px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  animation: stat-float 3s ease-in-out infinite;
}

.stat-card:hover {
  transform: translateY(-5px) scale(1.05);
  border-color: #ff8c00;
  box-shadow: 0 15px 30px rgba(255, 140, 0, 0.3);
}

.stat-number {
  font-family: 'Bebas Neue', cursive;
  font-size: 2rem;
  color: #ff8c00;
  text-shadow: 0 0 10px rgba(255, 140, 0, 0.5);
  line-height: 1;
}

.stat-label {
  font-size: 0.7rem;
  color: rgba(255, 255, 255, 0.8);
  font-weight: 700;
  letter-spacing: 1px;
  margin-top: 0.2rem;
}

/* Botón de inicio */
.start-btn {
  background: linear-gradient(135deg, #ff8c00, #ff4500);
  border: none;
  border-radius: 50px;
  color: white;
  font-size: 1.1rem;
  font-weight: 700;
  padding: 1rem 3rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  gap: 0.8rem;
  box-shadow: 0 15px 40px rgba(255, 140, 0, 0.4);
  text-transform: uppercase;
  letter-spacing: 2px;
  font-family: 'Bebas Neue', cursive;
  margin-top: 1rem;
}

.start-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 20px 50px rgba(255, 140, 0, 0.6);
  background: linear-gradient(135deg, #ffa500, #ff6347);
}

.btn-arrow {
  font-size: 1rem;
  transition: transform 0.3s ease;
}

.start-btn:hover .btn-arrow {
  transform: scale(1.2) rotate(15deg);
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

@keyframes float-basketball {
  0%, 100% {
    transform: translateY(0px) rotate(0deg);
  }
  25% {
    transform: translateY(-20px) rotate(90deg);
  }
  50% {
    transform: translateY(-10px) rotate(180deg);
  }
  75% {
    transform: translateY(-25px) rotate(270deg);
  }
}

@keyframes basketball-bounce {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
}

@keyframes stat-float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-3px);
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

/* Animación de entrada */
.bounce-enter-active {
  animation: bounce-in 1s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

@keyframes bounce-in {
  0% {
    transform: scale(0.8);
    opacity: 0;
  }
  50% {
    transform: scale(1.05);
    opacity: 0.8;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

/* Responsive */
@media (max-width: 768px) {
  .main-title {
    font-size: 2.2rem;
    letter-spacing: 2px;
    gap: 0.5rem;
  }
  
  .title-icon {
    font-size: 1.8rem;
  }
  
  .subtitle {
    font-size: 1rem;
    padding: 0 1rem;
    margin-bottom: 1.5rem;
  }
  
  .game-stats {
    gap: 1rem;
  }
  
  .stat-card {
    padding: 0.8rem 1rem;
    width: 85px;
    height: 70px;
  }
  
  .stat-number {
    font-size: 1.5rem;
  }
  
  .start-btn {
    padding: 0.8rem 2.5rem;
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .landing-content {
    padding: 0.5rem;
  }
  
  .main-title {
    font-size: 1.8rem;
    letter-spacing: 1px;
  }
  
  .main-icon {
    width: 70px;
    height: 70px;
  }
  
  .icon-symbol {
    font-size: 2rem;
  }
  
  .game-stats {
    gap: 0.8rem;
    margin: 1.5rem 0;
  }
  
  .stat-card {
    padding: 0.6rem 0.8rem;
    width: 70px;
    height: 60px;
  }
  
  .stat-number {
    font-size: 1.3rem;
  }
  
  .stat-label {
    font-size: 0.6rem;
  }
  
  .start-btn {
    padding: 0.7rem 2rem;
    font-size: 0.9rem;
  }
}

@media (max-height: 700px) {
  .main-icon {
    width: 70px;
    height: 70px;
    margin-bottom: 1rem;
  }
  
  .icon-symbol {
    font-size: 2rem;
  }
  
  .main-title {
    font-size: 2.2rem;
    margin-bottom: 0.8rem;
  }
  
  .subtitle {
    font-size: 1rem;
    margin-bottom: 1.5rem;
  }
  
  .game-stats {
    margin: 1.5rem 0;
  }
}
</style>