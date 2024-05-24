<template>
  <div class="barrier" @click="placeBarrier"></div>
</template>

<script>
export default {
  methods: {
    placeBarrier() {
      // Emitir evento para indicar que se debe colocar una barrera en esta posición
      this.$emit('placeBarrier');
    }
  }
}
</script>

<style scoped>
/* Estilos para la barrera */
.barrier {
  width: 50px;
  height: 10px; /* Ajustar según el diseño de la barrera */
  background-color: #000; /* Color de la barrera */
}
</style>
