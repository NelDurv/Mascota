<template>
  <div class="container">
    <h1 style="text-align: center; color: white">🐾 Elige tu mascota ideal 🐾</h1>

    <MascotaSelector
      :mascotas="listaMascotas"
      :seleccionadaId="mascotaSeleccionada?.id"
      @seleccionar="seleccionarMascota"
    />

    <MascotaCard
      v-if="mascotaSeleccionada"
      :mascota="mascotaSeleccionada"
      @cambiar-foto="cambiarFotoAleatoria"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import MascotaSelector from './components/MascotaSelector.vue'
import MascotaCard from './components/MascotaCard.vue'

const mascotaSeleccionada = ref(null)

const listaMascotas = ref([
  {
    id: 1,
    nombre: 'Copito',
    tipo: 'Cabra',
    edad: 3,
    vacunado: true,
    foto: 'cabra.jpg',
    fotosAlternativas: ['cabra.jpg', 'cabra2.jpg', 'cabra3.jpg'],
    caracteristicas: ['Saltarina', 'Curiosa'],
  },
  {
    id: 2,
    nombre: 'Alazan',
    tipo: 'Caballo',
    edad: 4,
    vacunado: true,
    foto: 'caballo.jpg',
    fotosAlternativas: ['caballo.jpg', 'caballo2.jpg', 'caballo3.jpg'],
    caracteristicas: ['Energético', 'Sociable'],
  },
  {
    id: 3,
    nombre: 'Tragon',
    tipo: 'Cerdo',
    edad: 2,
    vacunado: false,
    foto: 'cerdo.jpg',
    fotosAlternativas: ['cerdo.jpg', 'cerdo2.jpg', 'cerdo3.jpg'],
    caracteristicas: ['Glotón', 'Dormilón'],
  },
  {
    id: 4,
    nombre: 'Pipiola',
    tipo: 'Gallina',
    edad: 1,
    vacunado: true,
    foto: 'gallina.jpg',
    fotosAlternativas: ['gallina.jpg', 'gallina2.jpg', 'gallina3.jpg'],
    caracteristicas: ['Juguetona', 'Picoteadora'],
  },
  {
    id: 5,
    nombre: 'Pompón',
    tipo: 'Conejo',
    edad: 2,
    vacunado: true,
    foto: 'conejito.jpg',
    fotosAlternativas: ['conejito.jpg', 'conejito2.jpg', 'conejito3.jpg'],
    caracteristicas: ['Suavecito', 'Saltarín'],
  },
  {
    id: 6,
    nombre: 'Gruñon',
    tipo: 'Tigre',
    edad: 24,
    vacunado: true,
    foto: 'tigre.png',
    fotosAlternativas: ['tigre.png', 'tigreJugando.png', 'tigreNadando.png'],
    caracteristicas: ['Suave', 'Juguetón'],
  },
])

const seleccionarMascota = (mascota) => {
  mascotaSeleccionada.value = { ...mascota }
}

const cambiarFotoAleatoria = () => {
  if (mascotaSeleccionada.value?.fotosAlternativas) {
    const fotos = mascotaSeleccionada.value.fotosAlternativas
    const randomIndex = Math.floor(Math.random() * fotos.length)
    mascotaSeleccionada.value.foto = fotos[randomIndex]
  }
}

seleccionarMascota(listaMascotas.value[0])
</script>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}
</style>
