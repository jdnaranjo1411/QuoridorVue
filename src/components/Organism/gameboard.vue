<template>
  <div class="balls">
    <div class="game-board">
          <square :x="n" :y="n" :occupied="false" :selected="false" v-for="n in 81" :key="n"/>
        </div>
  </div>
</template>

<script setup>
import square from '../Atoms/square.vue';
import { onMounted, ref } from 'vue';
const useEffect = onMounted;


const board = ref([]); // Array para almacenar el tablero

useEffect(() => {
  for (let i = 0; i < 9; i++) {
    const row = [];
    for (let j = 0; j < 9; j++) {
      // Asignar coordenadas x e y a cada cuadrícula

      row.push({ i, j });
    }
    board.value.push(row);
  }
  console.log(board.value);
});
</script>

<style scoped>


.balls {
  display: flex;
  justify-content: center;
}

.game-board {
  display: grid;
  grid-template-columns: repeat(9, minmax(50px, 1fr));
}

.row {
  display: flex;
}
  
</style>
