<template>
  <button @click="$emit('click')" class="btn-cambiar-foto">
    🖼️ Cambiar foto de {{ nombre }}
  </button>
</template>

<script>
export default {
  name: 'BotonCambiarFoto',
  props: {
    nombre: String
  },
  emits: ['click']
}
</script>

<style scoped>
.btn-cambiar-foto {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border: none;
  color: white;
  padding: 10px 20px;
  border-radius: 30px;
  cursor: pointer;
  width: 100%;
  font-size: 1rem;
  transition: 0.3s;
}

.btn-cambiar-foto:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}
</style>