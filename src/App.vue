<!-- <template>
  <section class="QuoridorVue">
    <h1 class="Titulo_Inicio">Juega Quoridor</h1>
    <p>Instrucciones: En Quoridor, tu objetivo es llegar al lado opuesto del tablero antes que tu oponente. 
      Puedes moverte hacia adelante, atrás, izquierda o derecha, o colocar muros para bloquear su camino. 
      ¡Planea tus movimientos con cuidado y sé el primero en alcanzar la meta para ganar!</p>
      <br>
      <button @click="restart" class="quoridor__button">Iniciar Partida</button>
<br>
      <p v-if="ganador">{{ ganador }} ha ganado esta partida</p>
      <p>Juega: {{ Turno === 1 ? 'Jugador 1 ' : 'Jugador 2 ' }}</p>
<br>
    <Tablero
      :board="board"
      :player1="player1"
      :player2="player2"
      :obstacles="obstacles"
      @cell-click="handleCellClick"
    />
    <p>Juega: {{ Turno === 1 ? 'Jugador 1 ' : 'Jugador 2 ' }}</p>

    <br>
   <footer class="quoridor__footer">
    <br>
    </footer>
  </section>
</template>

<script>
import Tablero from './components/organisms/Tablero.vue';

export default {
  components: {
    Tablero
  },
  data() {
    return {
      board: this.createBoard(),
      player1: { x: 4, y: 0, color: 'red' },
      player2: { x: 4, y: 8, color: 'blue' },
      Turno: 1, // Turno de cada jugador
      obstacles: [], 
      ganador: null 
    }
  },
  methods: {
    createBoard() {
      return Array(9).fill().map(() => Array(9).fill(null));
    },
    restart() {
      this.board = this.createBoard();
      this.player1 = { x: 4, y: 0, color: 'red' };
      this.player2 = { x: 4, y: 8, color: 'blue' };
      this.Turno = 1; 
      this.obstacles = [];
      this.ganador = null;
    },
    handleCellClick(i, j) {
      if (this.ganador) return; 
      const Turno = this.Turno === 1 ? this.player1 : this.player2;

      if (this.isValidMove(i, j)) {
        Turno.x = j;
        Turno.y = i;
        this.checkGanador();
        if (!this.ganador) {
          this.Turno = this.Turno === 1 ? 2 : 1; // Alternar entre jugadores si no hay ganador
        }
      } else if (!this.isPlayer1(i, j) && !this.isPlayer2(i, j) && !this.isObstacle(i, j)) {
        this.placeObstacle(i, j);
        this.Turno = this.Turno === 1 ? 2 : 1; // Alternar entre jugadores
      }
    },
    isValidMove(i, j) {
      const Turno = this.Turno === 1 ? this.player1 : this.player2;
      const dx = Math.abs(j - Turno.x);
      const dy = Math.abs(i - Turno.y);
      return (dx === 1 && dy === 0) || (dx === 0 && dy === 1) && !this.isObstacle(i, j);
    },
    
    placeObstacle(i, j) {
      this.obstacles.push({ x: j, y: i });
    },
    isPlayer1(i, j) {
      return this.player1.x === j && this.player1.y === i;
    },
    isPlayer2(i, j) {
      return this.player2.x === j && this.player2.y === i;
    },
    isObstacle(i, j) {
      return this.obstacles.some(obstacle => obstacle.x === j && obstacle.y === i);
    },
    checkGanador() {
      if (this.player1.y === 8) {
        this.ganador = 'Jugador 1 (Rojo)';
      } else if (this.player2.y === 0) {
        this.ganador = 'Jugador 2 (Azul)';
      }
    }
  }
}
</script>

<style scoped>
.QuoridorVue {
  text-align: center;
  color: #000;
}

.quoridor__title {
  margin-bottom: 20px;
}

.quoridor__board {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

.quoridor__button {
  display: block;
  margin: 0 auto;
  padding: 10px 20px;
  background-color: #efc679;
  color: rgb(21, 21, 21);
  border: none;
  cursor: pointer;
}

.quoridor__button:hover {
  background-color: #f69c60;
}

.quoridor__footer {
  margin-top: 20px;
}
</style> -->

<template>
  <section class="QuoridorVue">
    <h1 class="Titulo_Inicio">Juega Quoridor</h1>
    <p>Instrucciones: En Quoridor, tu objetivo es llegar al lado opuesto del tablero antes que tu oponente.
      Puedes moverte hacia adelante, atrás, izquierda o derecha, o colocar muros para bloquear su camino.
      ¡Planea tus movimientos con cuidado y sé el primero en alcanzar la meta para ganar!</p>
    <br>
    <button @click="restart" class="quoridor__button">Iniciar Partida</button>
    <br>
    <p v-if="ganador">{{ ganador }} ha ganado esta partida</p>
    <p>Juega: {{ Turno === 1 ? 'Jugador 1 ' : 'Jugador 2 ' }}</p>
    <br>
    <Tablero :board="board" :player1="player1" :player2="player2" :obstacles="obstacles"
      @cell-click="handleCellClick" />
    <p>Juega: {{ Turno === 1 ? 'Jugador 1 ' : 'Jugador 2 ' }}</p>
    <br>
    <label>
      Orientación de la barrera:
      <select v-model="obstacleOrientation">
        <option value="horizontal">Horizontal</option>
        <option value="vertical">Vertical</option>
      </select>
    </label>
    <br>
    <footer class="quoridor__footer">
      <br>
    </footer>
  </section>
</template>

<script>
import Tablero from './components/organisms/Tablero.vue';

export default {
  components: {
    Tablero
  },
  data() {
    return {
      board: this.createBoard(),
      player1: { x: 4, y: 0, color: 'red' },
      player2: { x: 4, y: 8, color: 'blue' },
      Turno: 1,
      obstacles: [],
      obstacleOrientation: 'horizontal',
      ganador: null
    }
  },
  methods: {
    createBoard() {
      return Array(9).fill().map(() => Array(9).fill(null));
    },
    restart() {
      this.board = this.createBoard();
      this.player1 = { x: 4, y: 0, color: 'red' };
      this.player2 = { x: 4, y: 8, color: 'blue' };
      this.Turno = 1;
      this.obstacles = [];
      this.obstacleOrientation = 'horizontal';
      this.ganador = null;
    },
    handleCellClick(i, j) {
      if (this.ganador) return;
      const Turno = this.Turno === 1 ? this.player1 : this.player2;

      if (this.isValidMove(i, j)) {
        Turno.x = j;
        Turno.y = i;
        this.checkGanador();
        if (!this.ganador) {
          this.Turno = this.Turno === 1 ? 2 : 1; // Alternar entre jugadores si no hay ganador
        }
      } else if (this.canPlaceObstacle(i, j)) {
        this.placeObstacle(i, j);
        this.Turno = this.Turno === 1 ? 2 : 1; // Alternar entre jugadores
      }
    },
    isValidMove(i, j) {
      const Turno = this.Turno === 1 ? this.player1 : this.player2;
      const dx = Math.abs(j - Turno.x);
      const dy = Math.abs(i - Turno.y);
      return ((dx === 1 && dy === 0) || (dx === 0 && dy === 1)) && !this.isObstacle(i, j);
    },
    canPlaceObstacle(i, j) {
      if (this.obstacleOrientation === 'horizontal') {
        return j < 8 && !this.isObstacle(i, j) && !this.isObstacle(i, j + 1);
      } else {
        return i < 8 && !this.isObstacle(i, j) && !this.isObstacle(i + 1, j);
      }
    },
    placeObstacle(i, j) {
      if (this.obstacleOrientation === 'horizontal') {
        this.obstacles.push({ x: j, y: i, orientation: 'horizontal' });
        this.obstacles.push({ x: j + 1, y: i, orientation: 'horizontal' });
      } else {
        this.obstacles.push({ x: j, y: i, orientation: 'vertical' });
        this.obstacles.push({ x: j, y: i + 1, orientation: 'vertical' });
      }
    },
    isPlayer1(i, j) {
      return this.player1.x === j && this.player1.y === i;
    },
    isPlayer2(i, j) {
      return this.player2.x === j && this.player2.y === i;
    },
    isObstacle(i, j) {
      return this.obstacles.some(obstacle => obstacle.x === j && obstacle.y === i);
    },
    checkGanador() {
      if (this.player1.y === 8) {
        this.ganador = 'Jugador 1 (Rojo)';
      } else if (this.player2.y === 0) {
        this.ganador = 'Jugador 2 (Azul)';
      }
    }
  }
}
</script>

<style scoped>
.QuoridorVue {
  text-align: center;
  color: #000;
}

.quoridor__title {
  margin-bottom: 20px;
}

.quoridor__board {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

.quoridor__button {
  display: block;
  margin: 0 auto;
  padding: 10px 20px;
  background-color: #efc679;
  color: rgb(21, 21, 21);
  border: none;
  cursor: pointer;
}

.quoridor__button:hover {
  background-color: #f69c60;
}

.quoridor__footer {
  margin-top: 20px;
}
</style>
