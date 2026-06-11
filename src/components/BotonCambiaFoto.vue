<template>
  <button @click="$emit('click')" class="btn-cambiar-foto">
    🖼️ Cambiar foto de {{ nombre }}
  </button>
</template>

<script setup>
defineProps({
  nombre: String
})
defineEmits(['click'])
</script>

<style scoped>
/* tu estilo actual se mantiene igual */
</style>