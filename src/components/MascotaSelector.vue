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
.grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px,1fr)); gap: 15px; }
.mascota-option { background: #f8f9fa; border-radius: 15px; padding: 15px; cursor: pointer; }
.seleccionada { border: 3px solid #667eea; background: #e9ecef; }
</style>