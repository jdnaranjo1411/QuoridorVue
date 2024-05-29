<template>
  <section class="jugadorquoridor">
    <div :style="{ backgroundColor: color === 'red' ? 'red' : 'blue' }" class="bolita"></div>
    <p v-if="color === 'red'">Jugador 1</p>
    <p v-if="color === 'blue'">Jugador 2</p>
  </section>
</template>

<script>
export default {
  props: {
    color: String
  }
}
</script>

<style scoped>
.jugadorquoridor {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.bolita {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-bottom: 10px;
}
</style>