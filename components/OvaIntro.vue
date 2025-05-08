<template>
    <div class="w-full h-screen flex flex-col items-center justify-center text-white p-6 relative overflow-hidden">
      <!-- Fondo de actividad física con patrón y textura -->
      <div class="absolute inset-0 bg-gradient-to-br from-blue-700 to-indigo-900 z-0">
        <!-- Patrón de pista de atletismo -->
        <div class="absolute inset-0 opacity-10">
          <div class="absolute top-0 left-0 w-full h-8 border-b-4 border-white"></div>
          <div class="absolute top-16 left-0 w-full h-8 border-b-4 border-white"></div>
          <div class="absolute top-32 left-0 w-full h-8 border-b-4 border-white"></div>
          <div class="absolute top-48 left-0 w-full h-8 border-b-4 border-white"></div>
        </div>
      </div>
  
      <!-- Siluetas deportivas -->
      <div class="absolute inset-0 z-1 opacity-20 overflow-hidden">
        <!-- Silueta corredor -->
        <div class="absolute bottom-0 left-10 h-64 w-32">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 50 100" fill="white">
            <path d="M25,20 a8,8 0 1,0 0,0.1 M20,35 L25,30 L30,35 L28,55 L32,57 L30,65 L25,63 L20,65 L18,57 L22,55 L20,35 M18,40 L10,50 M32,40 L40,50 M22,65 L18,90 M28,65 L32,90" stroke="white" stroke-width="2" fill="none" />
          </svg>
        </div>
        
        <!-- Silueta ciclista -->
        <div class="absolute bottom-10 right-20 h-48 w-64">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 60" fill="white">
            <circle cx="25" cy="40" r="15" stroke="white" stroke-width="2" fill="none" />
            <circle cx="75" cy="40" r="15" stroke="white" stroke-width="2" fill="none" />
            <path d="M75,40 L60,10 M60,10 L35,30 M35,30 L25,40 M35,30 L50,25 M50,25 L75,40 M50,25 L50,15 L55,10" stroke="white" stroke-width="2" fill="none" />
          </svg>
        </div>
        
        <!-- Silueta nadador -->
        <div class="absolute top-20 left-1/3 h-32 w-64">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 120 30" fill="white">
            <path d="M10,15 C15,5 25,5 30,15 C35,25 45,25 50,15 C55,5 65,5 70,15 C75,25 85,25 90,15 C95,5 105,5 110,15" stroke="white" stroke-width="2" fill="none" />
          </svg>
        </div>
      </div>
      
      <!-- Animación de elementos deportivos -->
      <div class="absolute inset-0 overflow-hidden z-2">
        <!-- Pelotas y elementos deportivos animados -->
        <div v-for="n in 8" :key="n" 
             class="absolute w-8 h-8 rounded-full bg-white opacity-15"
             :style="`top: ${Math.random() * 100}%; left: ${Math.random() * 100}%; animation: float ${3 + n}s infinite ease-in-out`">
        </div>
      </div>
      
      <transition name="bounce">
        <div v-if="showContent" class="text-center space-y-6 max-w-xl relative z-10">
          <div class="flex justify-center mb-4">
            <div class="w-16 h-16 rounded-full bg-white flex items-center justify-center mb-2">
              <!-- Icono deportivo simple -->
              <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-blue-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
              </svg>
            </div>
          </div>
          
          <h1 class="text-4xl md:text-6xl font-bold tracking-tight">Actívate con el Deporte</h1>
          <p class="text-lg md:text-xl">
            Descubre cómo una vida activa transforma tu cuerpo y mente. ¡Muévete, vive mejor!
          </p>
          
          <!-- Iconos de deportes -->
          <div class="flex justify-center space-x-6 py-4">
            <div v-for="(deporte, index) in deportes" :key="index" 
                 class="w-12 h-12 rounded-full bg-white/20 flex items-center justify-center backdrop-blur-sm hover:bg-white/30 transition-all transform hover:scale-110 cursor-pointer">
              <span class="text-xl">{{ deporte.emoji }}</span>
            </div>
          </div>
          
          <button @click="startExperience" 
                  class="mt-6 px-8 py-4 bg-white text-blue-600 font-bold rounded-xl shadow-lg hover:bg-blue-100 transition-all transform hover:scale-105 hover:shadow-xl flex items-center justify-center group">
            <span>Empezar Ahora</span>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
            </svg>
          </button>
          
          <!-- Indicador de desplazamiento -->
          <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 -translate-y-16 animate-bounce opacity-70">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
            </svg>
          </div>
        </div>
      </transition>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue'
  import { useRouter } from 'vue-router'
  
  const showContent = ref(false)
  const router = useRouter()
  
  // Lista de deportes con sus emojis
  const deportes = ref([
    { nombre: 'Fútbol', emoji: '⚽' },
    { nombre: 'Baloncesto', emoji: '🏀' },
    { nombre: 'Tenis', emoji: '🎾' },
    { nombre: 'Natación', emoji: '🏊' },
    { nombre: 'Ciclismo', emoji: '🚴' }
  ])
  
  onMounted(() => {
    setTimeout(() => {
      showContent.value = true
    }, 800) // Delay para la animación de entrada
  })
  
  function startExperience() {
    router.push('/deportes') // Redirige a la sección principal
  }
  </script>
  
  <style scoped>
  /* Animación de entrada con rebote */
  .bounce-enter-active {
    animation: bounce-in 0.8s;
  }
  .bounce-leave-active {
    animation: bounce-in 0.5s reverse;
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
  
  /* Animación de elementos flotantes */
  @keyframes float {
    0% {
      transform: translateY(0px) rotate(0deg);
    }
    50% {
      transform: translateY(-20px) rotate(180deg);
    }
    100% {
      transform: translateY(0px) rotate(360deg);
    }
  }
  
  /* Agregamos una sutil animación de pulso para las siluetas */
  @keyframes pulse {
    0% {
      opacity: 0.15;
    }
    50% {
      opacity: 0.25;
    }
    100% {
      opacity: 0.15;
    }
  }
  
  /* Animación para las líneas de pista */
  @keyframes track-move {
    0% {
      transform: translateY(0);
    }
    100% {
      transform: translateY(16px);
    }
  }
  </style>
  