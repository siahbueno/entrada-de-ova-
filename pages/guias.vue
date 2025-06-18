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
            GUÍAS DE BALONCESTO
            <span class="title-icon">🏀</span>
          </h1>
          <p class="subtitle">Técnicas y estrategias para mejorar tu juego</p>
        </div>
        <div class="header-decoration"></div>
      </header>

      <!-- Contenido principal -->
      <main class="content-grid">
        <!-- Sección de técnicas de dribleo -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">🏀 TÉCNICAS DE DRIBLEO</h2>
          </div>
          <div class="card-content">
            <div class="guide-item">
              <h3>Dribleo bajo</h3>
              <p>Mantén el balón cerca del suelo con las rodillas flexionadas para mayor control y rapidez. Usa la palma hacia abajo y los dedos extendidos. Practica: driblar 30 segundos con cada mano, alternando, sin mirar el balón.</p>
            </div>
            <div class="guide-item">
              <h3>Cambio de mano</h3>
              <p>Cambia el balón de una mano a otra rápidamente para confundir al defensor. Usa el cuerpo para proteger el balón. Drill: realiza 20 crossovers (cambios frontales) seguidos, aumentando la velocidad.</p>
            </div>
            <div class="guide-item">
              <h3>Dribleo entre piernas</h3>
              <p>Pasa el balón entre las piernas para evadir al defensor. Mantén una pierna adelantada y usa un movimiento rápido de muñeca. Ejercicio: haz 10 dribleos entre piernas con cada mano, alternando lados.</p>
            </div>
            <div class="guide-item">
              <h3>Spin move</h3>
              <p>Gira sobre un pie para dejar atrás al defensor, protegiendo el balón con el cuerpo. Practica: combina un spin move con un cambio de dirección, repitiendo 15 veces por lado.</p>
            </div>
          </div>
        </section>

        <!-- Sección de consejos de tiro -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">🎯 CONSEJOS DE TIRO</h2>
          </div>
          <div class="card-content">
            <div class="guide-plan">
              <h3>Mejora tu precisión</h3>
              <ul class="guide-list">
                <li><strong>Postura:</strong> Pies alineados al aro, separados al ancho de hombros, rodillas ligeramente flexionadas.</li>
                <li><strong>Agarre:</strong> Sujeta el balón con los dedos, no con la palma, dejando un pequeño espacio bajo el balón.</li>
                <li><strong>Enfoque:</strong> Mira el centro del aro o el gancho trasero antes de lanzar. Mantén la vista fija.</li>
                <li><strong>Follow-through:</strong> Extiende el brazo completamente y flexiona la muñeca hacia abajo, como si metieras la mano en una jarra.</li>
                <li><strong>Drill:</strong> Lanza 50 tiros libres diarios, enfocándote en la técnica. Anota tus aciertos para medir progreso.</li>
                <li><strong>Tiro en suspensión:</strong> Salta verticalmente, lanzando en el punto más alto. Practica 20 tiros desde 3 metros, luego desde la línea de triples.</li>
              </ul>
            </div>
          </div>
        </section>

        <!-- Sección de estrategias defensivas -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">🛡️ ESTRATEGIAS DEFENSIVAS</h2>
          </div>
          <div class="card-content">
            <div class="guide-grid">
              <div class="guide-item">
                <h3>Postura defensiva</h3>
                <p>Rodillas flexionadas, espalda recta, pies separados al ancho de hombros. Mantén los brazos extendidos para bloquear pases. Drill: mantén la postura 1 minuto, moviéndote lateralmente.</p>
              </div>
              <div class="guide-item">
                <h3>Defensa al hombre</h3>
                <p>Sigue al atacante de cerca, manteniendo una distancia de un brazo. Usa pasos laterales rápidos. Ejercicio: defiende a un compañero en un 1 contra 1, sin dejar que pase por 30 segundos.</p>
              </div>
              <div class="guide-item">
                <h3>Robo de balón</h3>
                <p>Anticipa el movimiento del balón y usa un movimiento rápido de mano para interceptar. No bajes la guardia. Practica: enfrenta a un compañero driblando, intentando robar 5 veces en 1 minuto.</p>
              </div>
              <div class="guide-item">
                <h3>Bloqueo de tiros</h3>
                <p>Salta verticalmente con los brazos extendidos para bloquear sin cometer falta. Calcula el tiempo del salto. Drill: defiende tiros de un compañero, intentando bloquear 10 lanzamientos.</p>
              </div>
            </div>
          </div>
        </section>

        <!-- Sección de jugadas ofensivas -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">⚡ JUGADAS OFENSIVAS</h2>
          </div>
          <div class="card-content">
            <div class="guide-list">
              <div class="guide-item">
                <span class="guide-number">1</span>
                <p><strong>Pick-and-roll:</strong> Un jugador pone una pantalla (bloqueo) al defensor del portador del balón, luego rueda hacia el aro para recibir un pase. Practica con un compañero, ejecutando 10 repeticiones.</p>
              </div>
              <div class="guide-item">
                <span class="guide-number">2</span>
                <p><strong>Give-and-go:</strong> Pasa el balón a un compañero y corta rápidamente hacia el aro para recibir un pase de vuelta. Drill: realiza 15 give-and-go con un compañero en 2 minutos.</p>
              </div>
              <div class="guide-item">
                <span class="guide-number">3</span>
                <p><strong>Corte sin balón:</strong> Muévete sin balón para desmarcarte, usando cortes en V o hacia el aro. Ejercicio: practica cortes en un 3 contra 3, buscando recibir 5 pases.</p>
              </div>
              <div class="guide-item">
                <span class="guide-number">4</span>
                <p><strong>Pantalla perimetral:</strong> Colócate para bloquear al defensor de un tirador, liberándolo para un tiro abierto. Practica: ejecuta 10 pantallas para un compañero tirador.</p>
              </div>
            </div>
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
import { useRouter } from 'vue-router'

const router = useRouter()
const currentPage = ref(2) // ID de la página actual (GUÍAS)

const menuOptions = ref([
  { id: 1, icon: '📚', title: 'CONTENIDO', route: '/contenido' },
  { id: 2, icon: '🏀', title: 'GUIAS', route: '/guias' },
  { id: 3, icon: '🏃‍♂️', title: 'ACTIVIDADES', route: '/actividades' },
  { id: 4, icon: '📋', title: 'EVALUACION', route: '/evaluacion' },
  { id: 5, icon: '🎖️', title: 'CREDITOS', route: '/creditos' }
])

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
  const option = menuOptions.value.find(opt => opt.id === optionId)
  if (option?.route) {
    try {
      await router.push(option.route)
    } catch (error) {
      console.error('Error en navegación:', error)
    }
  }
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

/* Guías */
.guide-item {
  margin-bottom: 1.5rem;
  padding: 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 10px;
  border-left: 4px solid #ffd700;
}

.guide-item h3 {
  color: #ffd700;
  margin: 0 0 0.5rem;
  font-size: 1.2rem;
  font-weight: 700;
}

.guide-item p {
  color: rgba(255, 255, 255, 0.8);
  margin: 0;
  line-height: 1.5;
}

.guide-plan h3 {
  color: #ff8c00;
  font-size: 1.3rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.guide-list {
  list-style: none;
  padding: 0;
}

.guide-list li {
  color: rgba(255, 255, 255, 0.8);
  padding: 0.8rem;
  margin-bottom: 0.5rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 8px;
  border-left: 3px solid #ff8c00;
}

.guide-list strong {
  color: #ffd700;
}

.guide-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.guide-item {
  background: rgba(255, 255, 255, 0.05);
  padding: 1.5rem;
  border-radius: 15px;
  border: 1px solid rgba(255, 140, 0, 0.2);
  text-align: center;
  transition: all 0.3s ease;
}

.guide-item:hover {
  background: rgba(255, 140, 0, 0.1);
  border-color: #ff8c00;
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(255, 140, 0, 0.2);
}

.guide-number {
  background: linear-gradient(135deg, #ff8c00, #ffd700);
  color: white;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  flex-shrink: 0;
  box-shadow: 0 3px 10px rgba(255, 140, 0, 0.4);
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
  
  .guide-grid {
    grid-template-columns: 1fr;
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
}
</style>