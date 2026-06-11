<template>
  <div class="selector">
    <h2>🐾 Elige tu mascota</h2>
    <div class="grid">
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
  border-radius: 20px;
  padding: 20px;
  margin-bottom: 30px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}
.mascotas-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
  gap: 15px;
}
.mascota-option {
  background: #f8f9fa;
  border: 3px solid transparent;
  border-radius: 15px;
  padding: 15px;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s ease;
}
.seleccionada {
  border-color: #667eea;
  background: linear-gradient(135deg, #667eea20 0%, #764ba220 100%);
}
/* 🔥 ESTILOS PARA MINIATURAS */
.mascota-option img {
  width: 80px;            /* Tamaño fijo */
  height: 80px;           /* Tamaño fijo */
  object-fit: cover;      /* Recorta para llenar el círculo sin deformar */
  border-radius: 50%;     /* Forma redonda */
  margin-bottom: 10px;
}
h3 {
  font-size: 1rem;
  margin: 5px 0;
}
p {
  font-size: 0.8rem;
  color: #7f8c8d;
}

</style>