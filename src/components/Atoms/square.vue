<template>
  <div class="square">
    <span>
      {{ props.x }}, {{ props.y }}
    </span>
  </div>
</template>

<script setup>

const props = defineProps({
  x: Number,
  y: Number,
  occupied: Boolean,
  selected: Boolean
})

</script>

<style scoped>
/* Estilos específicos para la cuadrícula */
.square {
  /* Estilos de la cuadrícula */
  border: 1px solid blue;
  background: gray;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50px;
  height: 50px;
}
</style>

  