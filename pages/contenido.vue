```vue
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
            BALONCESTO
            <span class="title-icon">🏀</span>
          </h1>
          <p class="subtitle">El deporte de la canasta - Historia, técnicas y fundamentos</p>
        </div>
        <div class="header-decoration"></div>
      </header>

      <!-- Contenido principal -->
      <main class="content-grid">
        <!-- Sección de historia -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">📚 HISTORIA DEL BALONCESTO</h2>
          </div>
          <div class="card-content">
            <div class="history-item">
              <h3>Origen (1891)</h3>
              <p>Inventado por James Naismith, un profesor de educación física canadiense en Springfield, Massachusetts, como actividad de invierno para mantener a sus estudiantes activos en un gimnasio. El objetivo era lanzar un balón de fútbol a canastas de melocotones fijadas a 3.05 metros de altura.</p>
            </div>
            <div class="history-item">
              <h3>Primeros juegos</h3>
              <p>Los primeros partidos se jugaron con nueve jugadores por equipo y reglas simples. Las canastas tenían fondo, por lo que se necesitaba una escalera para recuperar el balón tras cada enceste. En 1893, se introdujeron aros metálicos y redes para facilitar el juego.</p>
            </div>
            <div class="history-item">
              <h3>Evolución moderna</h3>
              <p>El baloncesto se popularizó rápidamente en universidades y clubes. En 1936, debutó como deporte olímpico masculino en Berlín, y en 1976 se incluyó la categoría femenina. La NBA, fundada en 1946 como la Basketball Association of America (BAA), se convirtió en la liga profesional más prestigiosa del mundo.</p>
            </div>
            <div class="history-item">
              <h3>Impacto global</h3>
              <p>Gracias a jugadores icónicos como Michael Jordan, Magic Johnson y LeBron James, el baloncesto se globalizó. La FIBA, fundada en 1932, organiza competiciones internacionales como el Mundial de Baloncesto. Hoy, el deporte es jugado por millones en más de 200 países.</p>
            </div>
          </div>
        </section>

        <!-- Sección de características -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">🏀 CARACTERÍSTICAS DEL JUEGO</h2>
          </div>
          <div class="card-content">
            <div class="characteristics-plan">
              <h3>Datos básicos</h3>
              <ul class="characteristics-list">
                <li><strong>Jugadores:</strong> 5 por equipo en cancha, con hasta 7 sustitutos en la NBA y 5 en FIBA.</li>
                <li><strong>Duración:</strong> 4 períodos de 12 minutos en la NBA; 4 períodos de 10 minutos en FIBA. Se juega tiempo extra de 5 minutos en caso de empate.</li>
                <li><strong>Cancha:</strong> 28m x 15m (FIBA); 28.65m x 15.24m (NBA). La superficie suele ser de madera pulida en interiores.</li>
                <li><strong>Altura aro:</strong> 3.05 metros desde el suelo hasta el borde superior del aro, estándar en todas las competiciones.</li>
                <li><strong>Balón:</strong> Circunferencia de 75-78 cm (talla 7 para hombres, talla 6 para mujeres). Peso aproximado de 600-650 gramos.</li>
                <li><strong>Puntuación:</strong> 2 puntos por tiro dentro del arco de 6.75m (FIBA) o 7.24m (NBA), 3 puntos fuera de este, y 1 punto por tiro libre.</li>
              </ul>
            </div>
          </div>
        </section>

        <!-- Sección de fundamentos -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">🎯 FUNDAMENTOS TÉCNICOS</h2>
          </div>
          <div class="card-content">
            <div class="fundamentals-grid">
              <div class="fundamental-item">
                <h3>Dribleo</h3>
                <p>Control del balón con una mano mientras se mueve, manteniendo la vista arriba para leer el juego. Incluye técnicas como el cambio de mano, el dribleo bajo y el crossover para evadir defensores.</p>
              </div>
              <div class="fundamental-item">
                <h3>Tiro</h3>
                <p>Lanzamiento al aro con técnica precisa: pies alineados, rodillas flexionadas, codo bajo el balón, y seguimiento de muñeca (follow-through). Incluye tiros de media distancia, triples y mates.</p>
              </div>
              <div class="fundamental-item">
                <h3>Pase</h3>
                <p>Transferencia del balón a un compañero con precisión. Tipos principales: pase de pecho (rápido y directo), pase picado (para evitar defensores), pase por encima de la cabeza, y pase de béisbol para transiciones rápidas.</p>
              </div>
              <div class="fundamental-item">
                <h3>Defensa</h3>
                <p>Impedir el avance del atacante mediante una postura baja (rodillas flexionadas, pies separados), brazos activos para bloquear pases, y desplazamientos laterales rápidos. Incluye técnicas como el robo de balón y el bloqueo de tiros.</p>
              </div>
              <div class="fundamental-item">
                <h3>Rebote</h3>
                <p>Recuperar el balón tras un tiro fallado. Los rebotes ofensivos dan segundas oportunidades de ataque, mientras que los defensivos evitan que el rival anote. Requiere posicionamiento, salto y anticipación.</p>
              </div>
              <div class="fundamental-item">
                <h3>Pivote</h3>
                <p>Movimiento con un pie fijo para proteger el balón, crear espacio o engañar al defensor. Permite girar, buscar ángulos de pase o tiro, y es esencial para jugadores en la pintura.</p>
              </div>
              <div class="fundamental-item">
                <h3>Bloqueo</h3>
                <p>Técnica ofensiva donde un jugador se posiciona para obstaculizar el movimiento de un defensor, liberando a un compañero. Común en jugadas como el pick-and-roll o pick-and-pop.</p>
              </div>
              <div class="fundamental-item">
                <h3>Corte</h3>
                <p>Movimiento sin balón para desmarcarse del defensor y crear oportunidades de pase o tiro. Incluye cortes en V, cortes hacia el aro y cortes de fondo para aprovechar espacios.</p>
              </div>
              <div class="fundamental-item">
                <h3>Pantalla</h3>
                <p>Acción de posicionarse estáticamente para bloquear al defensor de un compañero, facilitando su movimiento. Puede ser una pantalla en el perímetro para un tirador o en la pintura para un corte al aro.</p>
              </div>
            </div>
          </div>
        </section>

        <!-- Sección de reglas -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">📋 REGLAS PRINCIPALES</h2>
          </div>
          <div class="card-content">
            <div class="rules-list">
              <div class="rule-item">
                <span class="rule-number">1</span>
                <p><strong>Dobles:</strong> No se puede driblear con ambas manos simultáneamente ni reiniciar el drible tras recoger el balón, salvo tras un pase o tiro. Viola esta regla resulta en pérdida de posesión.</p>
              </div>
              <div class="rule-item">
                <span class="rule-number">2</span>
                <p><strong>Pasos:</strong> Un jugador con el balón puede dar máximo 2 pasos sin driblear. Exceder esto, conocido como "traveling," concede el balón al equipo contrario.</p>
              </div>
              <div class="rule-item">
                <span class="rule-number">3</span>
                <p><strong>24 segundos:</strong> El equipo en posesión debe intentar un tiro al aro dentro de 24 segundos (NBA) o 24 segundos (FIBA). Si no lo hace, pierde la posesión.</p>
              </div>
              <div class="rule-item">
                <span class="rule-number">4</span>
                <p><strong>Zona de 3 puntos:</strong> Tiros desde más allá de la línea de 6.75m (FIBA) o 7.24m (NBA) valen 3 puntos. Dentro de esta línea, los tiros valen 2 puntos.</p>
              </div>
              <div class="rule-item">
                <span class="rule-number">5</span>
                <p><strong>Faltas personales:</strong> Contacto ilegal con un oponente. Un jugador con 5 faltas (FIBA) o 6 (NBA) es expulsado del partido. Las faltas pueden otorgar tiros libres al equipo contrario.</p>
              </div>
              <div class="rule-item">
                <span class="rule-number">6</span>
                <p><strong>3 segundos en la zona:</strong> Un jugador ofensivo no puede permanecer más de 3 segundos en la zona pintada (área bajo el aro) mientras su equipo tiene posesión.</p>
              </div>
              <div class="rule-item">
                <span class="rule-number">7</span>
                <p><strong>Falta técnica:</strong> Sanciones por conducta antideportiva, como protestar al árbitro o retrasar el juego. Otorga un tiro libre y posesión al equipo contrario.</p>
              </div>
            </div>
          </div>
        </section>

        <!-- Sección de posiciones -->
        <section class="content-card full-width">
          <div class="card-header">
            <h2 class="card-title">👥 POSICIONES DE JUEGO</h2>
          </div>
          <div class="card-content">
            <div class="positions-list">
              <div class="position-item">
                <h3>Base (Point Guard, 1)</h3>
                <p>El "director de orquesta" del equipo. Organiza jugadas, distribuye el balón y toma decisiones rápidas. Requiere visión de juego, habilidades de pase y dribleo. Ejemplo: Stephen Curry.</p>
              </div>
              <div class="position-item">
                <h3>Escolta (Shooting Guard, 2)</h3>
                <p>Especialista en anotar desde larga distancia y crear jugadas ofensivas. A menudo es un tirador de triples y puede driblear bajo presión. Ejemplo: Kobe Bryant.</p>
              </div>
              <div class="position-item">
                <h3>Alero (Small Forward, 3)</h3>
                <p>Jugador versátil que combina habilidades ofensivas y defensivas. Puede anotar desde fuera, penetrar al aro y defender múltiples posiciones. Ejemplo: LeBron James.</p>
              </div>
              <div class="position-item">
                <h3>Ala-Pívot (Power Forward, 4)</h3>
                <p>Fuerte en rebotes y juego interior, con capacidad para tiros de media distancia. A menudo participa en bloqueos y jugadas cerca del aro. Ejemplo: Kevin Garnett.</p>
              </div>
              <div class="position-item">
                <h3>Pívot (Center, 5)</h3>
                <p>El jugador más alto, encargado de dominar la zona pintada. Excelente en rebotes, bloqueos y anotaciones cerca del aro. También protege el aro defensivamente. Ejemplo: Shaquille O’Neal.</p>
              </div>
              <div class="position-item">
                <h3>Híbridos/Modernos</h3>
                <p>En el baloncesto actual, las posiciones son más fluidas. Jugadores como "point forwards" (bases con tamaño de alero) o "stretch fours" (ala-pívots tiradores) combinan roles tradicionales. Ejemplo: Giannis Antetokounmpo.</p>
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
const currentPage = ref(1) // ID de la página actual (CONTENIDO)

// Opciones del menú lateral
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

/* Historia */
.history-item {
  margin-bottom: 1.5rem;
  padding: 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 10px;
  border-left: 4px solid #ffd700;
}

.history-item h3 {
  color: #ffd700;
  margin: 0 0 0.5rem;
  font-size: 1.2rem;
  font-weight: 700;
}

.history-item p {
  color: rgba(255, 255, 255, 0.8);
  margin: 0;
  line-height: 1.5;
}

/* Características */
.characteristics-plan h3 {
  color: #ff8c00;
  font-size: 1.3rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.characteristics-list {
  list-style: none;
  padding: 0;
}

.characteristics-list li {
  color: rgba(255, 255, 255, 0.8);
  padding: 0.8rem;
  margin-bottom: 0.5rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 8px;
  border-left: 3px solid #ff8c00;
}

.characteristics-list strong {
  color: #ffd700;
}

/* Fundamentos */
.fundamentals-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.fundamental-item {
  background: rgba(255, 255, 255, 0.05);
  padding: 1.5rem;
  border-radius: 15px;
  border: 1px solid rgba(255, 140, 0, 0.2);
  text-align: center;
  transition: all 0.3s ease;
}

.fundamental-item:hover {
  background: rgba(255, 140, 0, 0.1);
  border-color: #ff8c00;
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(255, 140, 0, 0.2);
}

.fundamental-item h3 {
  color: #ff8c00;
  margin: 0 0 1rem;
  font-size: 1.2rem;
  font-weight: 700;
}

.fundamental-item p {
  color: rgba(255, 255, 255, 0.7);
  margin: 0;
  line-height: 1.4;
}

/* Reglas */
.rules-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.rule-item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 10px;
}

.rule-number {
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

.rule-item p {
  color: rgba(255, 255, 255, 0.8);
  margin: 0;
  line-height: 1.5;
}

/* Posiciones */
.positions-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.position-item {
  padding: 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 10px;
  border-left: 4px solid #ff8c00;
  transition: all 0.3s ease;
}

.position-item:hover {
  background: rgba(255, 140, 0, 0.1);
  border-left-color: #ffd700;
}

.position-item h3 {
  color: #ff8c00;
  margin: 0 0 0.5rem;
  font-size: 1.1rem;
  font-weight: 700;
}

.position-item p {
  color: rgba(255, 255, 255, 0.8);
  margin: 0;
  line-height: 1.5;
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
  
  .fundamentals-grid {
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
```