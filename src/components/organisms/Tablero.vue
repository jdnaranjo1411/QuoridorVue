<!-- <template>
  <section class="tablero_Quoridor">
      <section v-for="(row, i) in board" :key="i" class="quoridor__row">
          <section v-for="(cell, j) in row" :key="j" class="quoridor__cell" @click="handleClick(i, j)">
              <Jugador v-if="isPlayer1(i, j)" :color="player1.color" />
              <Jugador v-if="isPlayer2(i, j)" :color="player2.color" />
              <Obstaculo v-if="isObstacle(i, j)" />
          </section>
      </section>
  </section>
</template>

<script>
import Jugador from '../Atoms/Jugador.vue';
import Obstaculo from '../molecules/Obstaculo.vue';

export default {
  components: {
    Jugador,
    Obstaculo
  },
  props: {
      board: Array,
      player1: Object,
      player2: Object,
      obstacles: Array
  },
  methods: {
      handleClick(i, j) {
          this.$emit('cell-click', i, j);
      },
      isPlayer1(i, j) {
          return this.player1.x === j && this.player1.y === i;
      },
      isPlayer2(i, j) {
          return this.player2.x === j && this.player2.y === i;
      },
      isObstacle(i, j) {
          return this.obstacles.some(obstacle => obstacle.x === j && obstacle.y === i);
      }
  }
}
</script>


<style scoped>
.tablero_Quoridor {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

.quoridor__row {
  display: flex;
}

.quoridor__cell {
  width: 80px;
  height: 80px;
  border: 3px solid rgb(219, 22, 22);
  position: relative;
}

</style> -->

<template>
  <section class="tablero_Quoridor">
    <section v-for="(row, i) in board" :key="i" class="quoridor__row">
      <section v-for="(cell, j) in row" :key="j" class="quoridor__cell" @click="handleClick(i, j)">
        <Jugador v-if="isPlayer1(i, j)" :color="player1.color" />
        <Jugador v-if="isPlayer2(i, j)" :color="player2.color" />
        <Obstaculo v-for="obstacle in getObstacles(i, j)" :key="obstacle.orientation" :orientation="obstacle.orientation" />
      </section>
    </section>
  </section>
</template>

<script>
import Jugador from '../Atoms/Jugador.vue';
import Obstaculo from '../molecules/Obstaculo.vue';

export default {
  components: {
    Jugador,
    Obstaculo
  },
  props: {
    board: Array,
    player1: Object,
    player2: Object,
    obstacles: Array
  },
  methods: {
    handleClick(i, j) {
      this.$emit('cell-click', i, j);
    },
    isPlayer1(i, j) {
      return this.player1.x === j && this.player1.y === i;
    },
    isPlayer2(i, j) {
      return this.player2.x === j && this.player2.y === i;
    },
    getObstacles(i, j) {
      return this.obstacles.filter(obstacle => obstacle.x === j && obstacle.y === i);
    }
  }
}
</script>

<style scoped>
.tablero_Quoridor {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

.quoridor__row {
  display: flex;
}

.quoridor__cell {
  width: 80px;
  height: 80px;
  border: 3px solid rgb(219, 22, 22);
  position: relative;
}
</style>