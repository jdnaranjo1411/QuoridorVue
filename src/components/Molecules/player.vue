<template>
    <div
      class="player"
      :style="{ top: playerPosition.top + 'px', left: playerPosition.left + 'px' }"
      @click="movePlayer"
    >
      X
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        playerPosition: { top: 0, left: 0 }, // Posición inicial del jugador
        boardSize: { width: 9, height: 9 } // Tamaño del tablero
      };
    },
    methods: {
      movePlayer(event) {
        // Calcula la posición de la casilla en la que se hizo clic
        const squareSize = event.target.clientWidth;
        const x = Math.floor(event.offsetX / squareSize);
        const y = Math.floor(event.offsetY / squareSize);
  
        // Verifica si la casilla es válida y mueve al jugador si lo es
        if (x >= 0 && x < this.boardSize.width && y >= 0 && y < this.boardSize.height) {
          this.playerPosition.top = y * squareSize;
          this.playerPosition.left = x * squareSize;
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .player {
    position: absolute;
    width: 50px; /* Ajusta el tamaño según el tamaño de las casillas del tablero */
    height: 50px; /* Ajusta el tamaño según el tamaño de las casillas del tablero */
    background-color: red; /* Cambia el color según tus necesidades */
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 24px; /* Ajusta el tamaño de la "X" */
    color: white; /* Ajusta el color del texto */
  }
  </style>
  