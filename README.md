# 🐾 Mascota – Elige tu compañero ideal

<img width="651" height="957" alt="image" src="https://github.com/user-attachments/assets/2381f3fa-2000-48c2-a9ad-f7a5e2370e7e" />

Aplicación Vue 3 para explorar y seleccionar diferentes mascotas, cambiar sus fotos y conocer sus características.  
Proyecto de aprendizaje enfocado en **`<script setup>`**, componentes reutilizables, props, emits y diseño responsive.

---

## 📁 Estructura del proyecto
mascota/
├── public/ # Imágenes de las mascotas (cabra.jpg, caballo.jpg, ...)
├── src/
│ ├── assets/ # Estilos globales (main.css)
│ ├── components/
│ │ ├── MascotaSelector.vue
│ │ ├── MascotaCard.vue
│ │ ├── MascotaInfo.vue
│ │ ├── VacunadoBadge.vue
│ │ └── BotonCambiarFoto.vue
│ ├── App.vue # Componente raíz
│ └── main.js # Punto de entrada
├── index.html
├── package.json
└── vite.config.js


---

##  Etapas del proyecto

1. **Configuración inicial**  
   - Creación del proyecto con `npm create vue@latest` (Vite + Vue 3).  
   - Estructura de carpetas y archivos base.

2. **Definición de datos**  
   - Lista de mascotas en `App.vue` (nombre, tipo, edad, vacunado, fotos, características).  
   - Estado reactivo con `ref`.

3. **Componentes principales**  
   - `MascotaSelector`: grilla con miniaturas, emite evento `seleccionar`.  
   - `MascotaCard`: muestra la ficha completa, recibe `mascota` por props.  
   - Subcomponentes: `MascotaInfo`, `VacunadoBadge`, `BotonCambiarFoto`.

4. **Comunicación entre componentes**  
   - Props hacia abajo (`:mascotas`, `:mascota`).  
   - Emits hacia arriba (`@seleccionar`, `@cambiar-foto`).

5. **Renderización dinámica**  
   - `v-for` para listar mascotas y características.  
   - `v-if` / `v-else` para estado de vacunación.  
   - Atributos dinámicos (`:src`, `:class`).

6. **Estilos y responsive**  
   - CSS por componente (scoped).  
   - Grid de 3 columnas en escritorio, 2 en tablet, 1 en móvil.  
   - Corrección de desbordamientos y márgenes en pantallas pequeñas.

7. **Mejoras finales**  
   - Botón verde con texto negro, centrado y separado.  
   - Información en línea horizontal.  
   - Imagen principal 10% más pequeña.  
   - Título separado 5px de la imagen.

---
##  GitHub 

https://github.com/NelDurv/Mascota.git

https://github.com/NelDurv/Mascota/commit/8ded414c600477d26ee191c4e0d854b55d3bc3db


##  Cómo ejecutar

```bash
npm install
npm run dev

Tecnologías
Vue 3 (Composition API con <script setup>)

Vite

CSS moderno (Grid, Flexbox, media queries)
