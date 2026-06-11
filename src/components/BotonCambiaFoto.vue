<template>
  <button @click="$emit('click')" class="btn-cambiar-foto">
     Cambiar foto de {{ nombre }}
  </button>
</template>

<script setup>
defineProps({ nombre: String })
defineEmits(['click'])
</script>

<style scoped>
.btn-cambiar-foto {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border: none;
  color: white;
  padding: 12px 24px;
  border-radius: 60px;
  cursor: pointer;
  font-weight: bold;
  font-size: 1rem;
  transition: 0.25s;
  width: auto;
  min-width: 220px;
  display: block;
  margin: 20px auto 15px auto;
  text-align: center;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
.btn-cambiar-foto:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
  background: linear-gradient(135deg, #5a67d8 0%, #6b46c1 100%);
}
</style>