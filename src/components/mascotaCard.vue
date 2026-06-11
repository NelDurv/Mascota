<template>
  <div class="card" v-if="mascota">
    <h2>{{ mascota.nombre }}</h2>
    <img :src="mascota.foto" :alt="mascota.nombre" class="pet-img" />
    <p>Tipo: {{ mascota.tipo }}</p>
    <p>Edad: {{ mascota.edad }} meses</p>
    <p>Vacunado: {{ mascota.vacunado ? '✅ Sí' : '❌ No' }}</p>
    <button @click="$emit('cambiar-foto')">🖼️ Cambiar foto</button>
  </div>
</template>

<script setup>
defineProps(['mascota'])
defineEmits(['cambiar-foto'])
</script>

<style scoped>
.card { background: white; border-radius: 28px; padding: 20px; margin-top: 20px; }
.pet-img { width: 100%; height: 300px; object-fit: cover; border-radius: 20px; }
button { background: #667eea; color: white; border: none; padding: 10px; border-radius: 30px; cursor: pointer; }
</style>