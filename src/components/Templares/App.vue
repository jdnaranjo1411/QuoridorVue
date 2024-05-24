<template>
  <div id="app">
    <!-- Componente del juego -->
    <!-- <Game /> -->

    <!-- Barra de herramientas -->
    <Toolbar />

    <gameboard />
    <!-- Jugador -->
  </div>
</template>

<script>
// Importa los componentes
import Game from '@/components/Organism/game.vue'
import Toolbar from '@/components/Organism/toolbar.vue' 
import gameboard from '@/components/Organism/gameboard.vue'
export default {
  components: {
    Game,
    Toolbar,
    gameboard
  }
}
</script>

<style src="./AppStyles.css"></style>

