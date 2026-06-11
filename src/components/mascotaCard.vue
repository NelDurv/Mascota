<template>
  <div class="card" v-if="mascota">
    <div class="card-header">
      <h1> {{ mascota.nombre }} </h1>
    </div>

    <img 
      :src="mascota.foto" 
      :alt="mascota.nombre" 
      class="pet-img"
      @error="manejarErrorImagen"
    />

    <div class="pet-info">
      <!-- Datos en línea horizontal -->
      <div class="info-row-horizontal">
        <div class="info-item">
          <span class="label">Nombre:</span>
          <span class="value">{{ mascota.nombre }}</span>
        </div>
        <div class="info-item">
          <span class="label"> Tipo:</span>
          <span class="value">{{ mascota.tipo }}</span>
        </div>
        <div class="info-item">
          <span class="label"> Edad:</span>
          <span class="value">{{ mascota.edad }} meses</span>
        </div>
        <div class="info-item">
          <span class="label"> Vacunado:</span>
          <span class="value">
            <span :class="['vacunado-badge', mascota.vacunado ? 'si' : 'no']">
              {{ mascota.vacunado ? ' Sí' : ' No' }}
            </span>
          </span>
        </div>
      </div>

      <!-- Características (siguen igual) -->
      <div class="caracteristicas">
        <h3> Características</h3>
        <ul>
          <li v-for="(caract, index) in mascota.caracteristicas" :key="index">
            {{ caract }}
          </li>
        </ul>
      </div>
    </div>

    <button class="btn-cambiar-foto" @click="$emit('cambiar-foto')">
      Cambiar foto de {{ mascota.nombre }}
    </button>

    <div class="footer">
       Todos nuestros animales son bebés 
    </div>
  </div>
</template>

<script setup>
defineProps({
  mascota: {
    type: Object,
    required: true
  }
})

defineEmits(['cambiar-foto'])

const manejarErrorImagen = (event) => {
  event.target.src = 'https://placehold.co/400x300?text=Imagen+no+disponible'
  console.warn('Error al cargar la imagen')
}
</script>

<style scoped>
.card {
  max-width: 550px;
  margin: 0 auto;
  background: white;
  border-radius: 32px;
  box-shadow: 0 20px 35px -10px rgba(0,0,0,0.25);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.card-header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 20px;
  text-align: center;
  margin-bottom: 5px;  /* Separación de 5px con la imagen */
}

.card-header h1 {
  margin: 0;
  font-size: 1.6rem;   /* Ligeramente más pequeño para reducir altura */
  font-weight: 600;
}

.pet-img {
  width: 90%;          /* 10% más pequeño que el ancho completo */
  max-width: 90%;
  height: auto;
  max-height: 315px;   /* 350px - 10% = 315px */
  object-fit: contain;
  background: #f4f4f4;
  display: block;
  margin: 0 auto;      /* Centrado horizontal */
  border-radius: 16px; /* Opcional: esquinas redondeadas */
}

.pet-info {
  padding: 20px 24px;  /* Reducido de 24px 28px para menor altura */
}

/* Nueva disposición horizontal de los datos */
.info-row-horizontal {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 12px;
  margin-bottom: 20px;
  background: #f8fafc;
  padding: 12px 16px;
  border-radius: 20px;
}

.info-item {
  flex: 1;
  min-width: 120px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 4px;
}

.label {
  font-weight: 700;
  color: #2c3e50;
  font-size: 0.85rem;
}

.value {
  color: #2c3e50;
  font-size: 0.95rem;
  font-weight: 500;
}

.vacunado-badge {
  display: inline-block;
  padding: 4px 10px;
  border-radius: 40px;
  font-size: 0.75rem;
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

.caracteristicas {
  margin-top: 10px;
  background: #f8fafc;
  border-radius: 20px;
  padding: 12px 16px;
}
.caracteristicas h3 {
  margin-top: 0;
  margin-bottom: 10px;
  color: #2c3e50;
  font-size: 1.1rem;
}
ul {
  list-style: none;
  padding-left: 0;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}
li {
  background: white;
  padding: 5px 12px;
  border-radius: 30px;
  font-size: 0.85rem;
}

.btn-cambiar-foto {
  background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%);
  border: none;
  color: #000000;
  font-weight: bold;
  padding: 10px 20px;
  border-radius: 60px;
  cursor: pointer;
  font-size: 0.95rem;
  transition: all 0.25s ease;
  width: auto;
  min-width: 200px;
  display: block;
  margin: 0 auto 12px auto;
  text-align: center;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
.btn-cambiar-foto:hover {
  transform: translateY(-2px);
  background: linear-gradient(135deg, #27ae60 0%, #1e8449 100%);
}

.footer {
  background: #ecf0f1;
  padding: 12px;
  text-align: center;
  font-size: 0.75rem;
  color: #4a5568;
}

/* Responsive: para pantallas pequeñas, evitar que la tarjeta quede pegada a la derecha */
@media (max-width: 640px) {
  .card {
    margin: 0 16px;    /* Márgenes laterales en móvil para centrar */
    max-width: calc(100% - 32px);
  }
  .info-row-horizontal {
    flex-direction: column;
    align-items: stretch;
  }
  .info-item {
    flex-direction: row;
    justify-content: space-between;
    text-align: left;
    gap: 8px;
  }
  .label {
    min-width: 80px;
  }
  .pet-img {
    width: 95%;
    max-width: 95%;
  }
}
</style>