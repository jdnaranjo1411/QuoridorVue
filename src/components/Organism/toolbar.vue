<template>
    <div class="toolbar">
      <!-- Aquí se usan los botones con la clase de estilo correspondiente -->
      <Button buttonClass="button--restart" @click="restartGame">Restart</Button>
      <Button buttonClass="button--surrender" @click="surrender">Surrender</Button>
      <Button buttonClass="button--back" @click="backMovement">Back</Button>
      <Button buttonClass="button--forward" @click="forwardMovement">Forward</Button>
    </div>
  </template>
  
  <script>
  import Button from '@/components/Atoms/button.vue';
  
  export default {
    components: {
      Button
    },
    methods: {
      restartGame() {
        // Lógica para reiniciar el juego
      },
      surrender() {
        // Lógica para rendirse en el juego
      },
      backMovement() {
        // Lógica para retroceder un movimiento en el juego
      },
      forwardMovement() {
        // Lógica para avanzar un movimiento en el juego
      }
    }
  }
  </script>
  
  <style scoped>
  /* Estilos para el organismo Toolbar */
  .toolbar {
    display: flex;
    justify-content: space-around;
    margin-top: 20px;
}
  </style>
  
  