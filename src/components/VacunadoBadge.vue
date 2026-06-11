<template>
  <span :class="['vacunado-badge', vacunado ? 'si' : 'no']">
    {{ vacunado ? ' Sí, está vacunado' : ' No vacunado' }}
  </span>
</template>

<script setup>
defineProps({
  vacunado: {
    type: Boolean,
    required: true
  }
})
</script>

<style scoped>
.vacunado-badge {
  display: inline-block;
  padding: 5px 15px;
  border-radius: 40px;
  font-weight: bold;
}
.si {
  background: #2ecc71;
  color: white;
}
.no {
  background: #e74c3c;
  color: white;
}
</style>