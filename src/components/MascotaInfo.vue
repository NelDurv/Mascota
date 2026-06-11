<template>
  <div class="pet-info">
    <!-- Datos básicos -->
    <div class="info-row">
      <span class="label">🐕 Nombre:</span>
      <span class="value">{{ mascota.nombre }}</span>
    </div>
    
    <div class="info-row">
      <span class="label">🐱 Tipo:</span>
      <span class="value">{{ mascota.tipo }}</span>
    </div>
    
    <div class="info-row">
      <span class="label">📅 Edad:</span>
      <span class="value">{{ mascota.edad }} meses</span>
    </div>
    
    <div class="info-row">
      <span class="label">💉 Vacunado:</span>
      <VacunadoBadge :vacunado="mascota.vacunado" />
    </div>

    <!-- Características con v-for -->
    <div class="caracteristicas">
      <h3>🌟 Características</h3>
      <ul>
        <li v-for="(caract, index) in mascota.caracteristicas" :key="index">
          {{ caract }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import VacunadoBadge from './VacunadoBadge.vue'

export default {
  name: 'MascotaInfo',
  components: { VacunadoBadge },
  props: {
    mascota: {
      type: Object,
      required: true
    }
  }
}
</script>