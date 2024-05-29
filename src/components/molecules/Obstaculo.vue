<!-- <template>
  <section class="obstaculosquoridor"></section>
</template>

<script>
export default {}
</script>

<style scoped>
.obstaculosquoridor{
  width: 200%;
  height: 5px;
  background-color: black; /* Mejor contraste para visualización */
}
</style> -->

<template>
  <div :class="['obstaculo', orientationClass]"></div>
</template>

<script>
export default {
  props: {
    orientation: {
      type: String,
      default: 'horizontal'
    }
  },
  computed: {
    orientationClass() {
      return this.orientation === 'horizontal' ? 'horizontal' : 'vertical';
    }
  }
}
</script>

<style scoped>
.obstaculo {
  position: absolute;
  background-color: black;
}

.obstaculo.horizontal {
  width: 80px; /* Double the cell width */
  height: 5px;
  top: -5px; /* Centering the obstacle within the cell */
  left: -0px; /* Centering the obstacle spanning two cells */
}

.obstaculo.vertical {
  width: 5px;
  height: 80px; /* Double the cell height */
  top: px; /* Centering the obstacle spanning two cells */
  left: -5px; /* Centering the obstacle within the cell */
}
</style>

