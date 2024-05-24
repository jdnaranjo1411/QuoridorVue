<template>
  <button :class="buttonClass" @click="$emit('click')">
    <slot></slot>
  </button>
</template>

<script setup>
  const props = defineProps ({
    buttonClass: String // Clase de estilo para el botón
}) 
</script>

<style scoped>
/* Estilos básicos para todos los botones */
button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>

  