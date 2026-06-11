<template>
  <div class="selector">
    <h2> Elige tu mascota</h2>
    <div class="mascotas-grid">
      <div 
        v-for="pet in mascotas" 
        :key="pet.id"
        class="mascota-option"
        :class="{ seleccionada: seleccionadaId === pet.id }"
        @click="$emit('seleccionar', pet)"
      >
        <img :src="pet.foto" :alt="pet.nombre" />
        <h3>{{ pet.nombre }}</h3>
        <p>{{ pet.tipo }}</p>
      </div>
    </div>
  </div>
</template>


<script setup>
defineProps(['mascotas', 'seleccionadaId'])
defineEmits(['seleccionar'])
</script>

<style scoped>
.selector {
  background: white;
  border-radius: 32px;
  padding: 24px 20px;
  margin-bottom: 30px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.1);
  max-width: 1000px;
  margin-left: auto;
  margin-right: auto;
}

.selector h2 {
  text-align: center;
  font-size: 1.6rem;
  color: #2c3e50;
  margin-bottom: 24px;
  font-weight: 600;
}

/*  GRILLA DE EXACTAMENTE 3 COLUMNAS en pantallas grandes */
.mascotas-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);  /* 3 columnas de igual ancho */
  gap: 20px;
  justify-items: center;
  align-items: start;
}

/* En pantallas medianas (tablets) → 2 columnas */
@media (max-width: 768px) {
  .mascotas-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* En pantallas muy pequeñas (móviles) → 1 columna */
@media (max-width: 480px) {
  .mascotas-grid {
    grid-template-columns: 1fr;
  }
}

.mascota-option {
  background: #f8f9fa;
  border-radius: 24px;
  padding: 16px 12px;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s;
  width: 100%;
  max-width: 220px;      /* Opcional: evita que se estiren demasiado */
  border: 2px solid transparent;
}

.mascota-option:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
}

.seleccionada {
  border-color: #667eea;
  background: #f0f2ff;
}

.mascota-option img {
  width: 100px;          /* Tamaño fijo para uniformidad */
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 12px;
  border: 2px solid white;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.mascota-option h3 {
  font-size: 1rem;
  margin: 8px 0 4px;
  color: #2c3e50;
}

.mascota-option p {
  font-size: 0.8rem;
  color: #7f8c8d;
}



</style>