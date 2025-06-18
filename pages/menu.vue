<template>
  <div class="sports-menu-container">
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
      <div v-for="n in 4" :key="n" 
           class="floating-ball"
           :style="`top: ${Math.random() * 80 + 10}%; left: ${Math.random() * 80 + 10}%; animation-delay: ${n * 1.2}s`">
        🏀
      </div>
    </div>

    <!-- Header deportivo -->
    <header class="sports-header">
      <div class="header-content">
        <h1 class="main-title">
          <span class="title-icon">🏆</span>
          MENÚ PRINCIPAL
          <span class="title-icon">🏆</span>
        </h1>
        <p class="subtitle">Selecciona tu categoría con doble click</p>
      </div>
    </header>

    <!-- Menú principal -->
    <main class="menu-grid">
      <div 
        v-for="option in menuOptions" 
        :key="option.id"
        class="menu-option" 
        @click="selectOption(option.id)" 
        @dblclick="navigateToPage(option.id)" 
        :class="{ active: selectedOption === option.id }"
      >
        <div class="option-icon">{{ option.icon }}</div>
        <h3 class="option-title">{{ option.title }}</h3>
        <div class="option-overlay"></div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

// Composables de Nuxt
const router = useRouter()

// Estado reactivo
const selectedOption = ref(null)

// Opciones del menú con iconos de baloncesto
const menuOptions = ref([
  { id: 1, icon: '📚', title: 'CONTENIDO', route: '/contenido' },
  { id: 2, icon: '🏀', title: 'GUIAS', route: '/guias' },
  { id: 3, icon: '🏃‍♂️', title: 'ACTIVIDADES', route: '/actividades' },
  { id: 4, icon: '📋', title: 'EVALUACION', route: '/evaluacion' },
  { id: 5, icon: '🎖️', title: 'CREDITOS', route: '/creditos' }
])

// Métodos
function selectOption(optionId) {
  console.log('Selected option ID:', optionId) // Debug: Confirm click
  selectedOption.value = optionId
}

function navigateToPage(optionId) {
  console.log('Double-clicked option ID:', optionId) // Debug: Confirm double-click
  const option = menuOptions.value.find(opt => opt.id === optionId)
  if (option?.route) {
    console.log('Attempting to navigate to:', option.route) // Debug: Log route
    router.push(option.route).then(() => {
      console.log('Navigation successful to:', option.route) // Debug: Success
      selectedOption.value = optionId // Update selected option
    }).catch(error => {
      console.error('Navigation failed to:', option.route, 'Error:', error) // Debug: Failure
      alert(`No se pudo navegar a ${option.title}. Verifica que la página exista. Error: ${error.message}`)
    })
  } else {
    console.warn('No route defined for option ID:', optionId) // Debug: Missing route
    alert(`No hay ruta definida para ${option?.title || 'esta opción'}.`)
  }
}

// Meta tags para SEO (Nuxt)
useSeoMeta({
  title: 'Menú Principal - Plataforma Deportiva',
  description: 'Accede a contenido, guías, actividades y evaluaciones deportivas',
  ogTitle: 'Menú Principal - Plataforma Deportiva',
  ogDescription: 'Tu portal deportivo completo'
})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Roboto:wght@400;700;900&display=swap');

.sports-menu-container {
  height: 100vh;
  background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 50%, #0f1419 100%);
  position: relative;
  overflow: hidden;
  font-family: 'Roboto', sans-serif;
  display: flex;
  flex-direction: column;
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
  opacity: 0.2;
  filter: drop-shadow(0 0 10px rgba(255, 140, 0, 0.5));
}

/* Header */
.sports-header {
  text-align: center;
  padding: 1.5rem 1rem 1rem;
  position: relative;
  z-index: 10;
  flex-shrink: 0;
}

.header-content {
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  backdrop-filter: blur(15px);
  border: 2px solid rgba(255, 140, 0, 0.3);
  border-radius: 15px;
  padding: 1.5rem;
  box-shadow: 0 15px 35px rgba(255, 140, 0, 0.4);
}

.main-title {
  font-family: 'Bebas Neue', cursive;
  font-size: clamp(1.8rem, 4vw, 2.8rem);
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
  margin: 0.8rem 0 0;
  opacity: 0.9;
  font-weight: 400;
}

/* Menú Grid */
.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  padding: 1rem;
  max-width: 1000px;
  margin: 0 auto;
  position: relative;
  z-index: 10;
  flex: 1;
  align-content: center;
}

.menu-option {
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  backdrop-filter: blur(15px);
  border-radius: 15px;
  padding: 1.5rem;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  border: 2px solid rgba(255, 140, 0, 0.3);
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  user-select: none;
  aspect-ratio: 1;
  min-height: 120px;
  box-shadow: 0 8px 25px rgba(255, 140, 0, 0.2);
}

.menu-option:hover {
  transform: translateY(-5px) scale(1.02);
  border-color: #ff8c00;
  box-shadow: 0 15px 30px rgba(255, 140, 0, 0.4);
  background: linear-gradient(145deg, rgba(255, 140, 0, 0.15), rgba(255, 140, 0, 0.1));
}

.menu-option.active {
  border-color: #ffd700;
  background: linear-gradient(145deg, rgba(255, 215, 0, 0.2), rgba(255, 215, 0, 0.1));
  box-shadow: 0 10px 25px rgba(255, 215, 0, 0.4);
}

.menu-option:hover::after {
  content: "Doble click para continuar";
  position: absolute;
  bottom: 8px;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0, 0, 0, 0.8);
  color: #ff8c00;
  padding: 0.2rem 0.6rem;
  border-radius: 10px;
  font-size: 0.7rem;
  font-weight: 600;
  opacity: 0;
  animation: fadeInUp 0.3s ease forwards;
  white-space: nowrap;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateX(-50%) translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }
}

.option-icon {
  font-size: clamp(2rem, 5vw, 3rem);
  margin-bottom: 0.5rem;
  filter: drop-shadow(0 0 15px rgba(255, 140, 0, 0.5));
}

.option-title {
  font-family: 'Bebas Neue', cursive;
  font-size: clamp(1rem, 2.5vw, 1.3rem);
  font-weight: 400;
  color: #ffffff;
  margin: 0;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
  letter-spacing: 2px;
}

.option-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, transparent, rgba(255, 140, 0, 0.1), transparent);
  transform: translateX(-100%);
  transition: transform 0.6s ease;
}

.menu-option:hover .option-overlay {
  transform: translateX(100%);
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

@keyframes texture-move {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(50px);
  }
}

/* Responsive para pantallas muy pequeñas */
@media (max-height: 600px) {
  .sports-header {
    padding: 0.8rem 1rem 0.5rem;
  }
  
  .header-content {
    padding: 1rem;
  }
  
  .menu-grid {
    gap: 1rem;
    padding: 0.8rem;
  }
  
  .menu-option {
    padding: 1rem;
    min-height: 100px;
  }
}

@media (max-width: 768px) {
  .menu-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }
  
  .title-icon {
    font-size: 1.8rem;
  }
  
  .main-title {
    gap: 0.5rem;
    letter-spacing: 2px;
  }
}

@media (max-width: 480px) {
  .menu-grid {
    grid-template-columns: 1fr 1fr;
    gap: 0.8rem;
    padding: 0.8rem;
  }
  
  .menu-option {
    padding: 1rem;
    border-radius: 12px;
  }
  
  .main-title {
    letter-spacing: 1px;
  }
  
  .title-icon {
    font-size: 1.5rem;
  }
}

/* Para pantallas muy anchas */
@media (min-width: 1200px) {
  .menu-grid {
    grid-template-columns: repeat(5, 1fr);
    max-width: 1200px;
  }
}
</style>