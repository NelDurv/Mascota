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

.card {
  max-width: 600px;
  margin: 0 auto;
  background: white;
  border-radius: 28px;
  box-shadow: 0 20px 35px -10px rgba(0,0,0,0.3);
  overflow: hidden;
}

.card-header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 20px;
  text-align: center;
}

/* 🔥 NUEVOS ESTILOS PARA LA IMAGEN PRINCIPAL */
.pet-img {
  width: 100%;           /* Ocupa todo el ancho del contenedor */
  max-width: 100%;       /* Evita que se desborde */
  height: auto;          /* Altura automática para mantener proporción */
  max-height: 400px;     /* Límite opcional de altura */
  object-fit: contain;   /* Muestra la imagen completa sin recortar */
  background: #e9ecef;
  display: block;        /* Elimina espacio extra debajo de la imagen */
  margin: 0 auto;
}

/* Opcional: si prefieres que la imagen cubra el espacio (recortando) usa object-fit: cover */
/* En ese caso, fija height: 300px; object-fit: cover; */

.pet-info {
  padding: 25px;
}

/* Resto de tus estilos para .info-row, .label, etc. se mantienen */
.footer {
  background: #ecf0f1;
  padding: 15px;
  text-align: center;
}

</style>