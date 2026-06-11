<template>
  <span 
    :class="['vacunado-badge', vacunado ? 'vacunado-si' : 'vacunado-no']"
  >
    {{ vacunado ? '✅ Sí, está vacunado' : '❌ No vacunado' }}
  </span>
</template>

<script>
export default {
  name: 'VacunadoBadge',
  props: {
    vacunado: {
      type: Boolean,
      required: true
    }
  }
}
</script>