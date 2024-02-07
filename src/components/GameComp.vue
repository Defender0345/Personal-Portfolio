<script>
export default {
  data() {
    return {
      cells: Array(9).fill(null),
      circleTurn: false,
      showWinningMessage: false,
      winningMessage: '',
      WINNING_COMBINATIONS: [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
      ]
    }
  },
  methods: {
    handleClick(index) {
      if (!this.cells[index]) {
        this.cells.splice(index, 1, this.circleTurn ? 'circle' : 'x')
        if (this.checkWin()) {
          this.endGame(`${this.circleTurn ? "O's" : "X's"} Wins!`)
        } else if (this.isDraw()) {
          this.endGame('Draw!')
        } else {
          this.swapTurns()
          this.setBoardHoverClass()
        }
      }
    },
    checkWin() {
      return this.WINNING_COMBINATIONS.some((combination) => {
        const [a, b, c] = combination
        return this.cells[a] && this.cells[a] === this.cells[b] && this.cells[a] === this.cells[c]
      })
    },
    isDraw() {
      return this.cells.every((cell) => cell !== null)
    },
    endGame(message) {
      this.winningMessage = message
      this.showWinningMessage = true
    },
    restartGame() {
      this.cells = Array(9).fill(null)
      this.circleTurn = false
      this.showWinningMessage = false
      this.winningMessage = ''
      this.setBoardHoverClass()
    },
    swapTurns() {
      this.circleTurn = !this.circleTurn
    },
    setBoardHoverClass() {
      this.board.classList.remove(this.X_CLASS)
      this.board.classList.remove(this.CIRCLE_CLASS)
      if (this.circleTurn) {
        this.board.classList.add(this.CIRCLE_CLASS)
      } else {
        this.board.classList.add(this.X_CLASS)
      }
    }
  }
}
</script>

<template>
  <h1>Let's Play Some Tick Tack Toe!</h1>
  <div class="board" id="board">
    <div
      class="cell"
      v-for="(cell, index) in cells"
      :key="index"
      @click="handleClick(index)"
      :class="{
        x: cell === 'x',
        circle: cell === 'circle',
        'hover-x': !circleTurn && cell === null,
        'hover-circle': circleTurn && cell === null
      }"
      data-cell
    ></div>
  </div>
  <div class="winning-message" id="winningMessage" v-if="showWinningMessage">
    <div data-winning-message-text>{{ winningMessage }}</div>
    <button id="restartButton" @click="restartGame">Restart</button>
  </div>
</template>

<style lang="scss">
// *,
// *::after,
// *::before {
//   box-sizing: border-box;
// }

:root {
  --cell-size: 100px;
  --mark-size: calc(var(--cell-size) * 0.9);
}

h1 {
  font-size: 2rem;
  display: block;
  padding-top: 97px;
  text-align: center;
  font-weight: 100;
  text-transform: uppercase;
}

.board {
  width: 100vw;
  height: 80vh;
  display: grid;
  justify-content: center;
  align-content: center;
  justify-items: center;
  align-items: center;
  grid-template-columns: repeat(3, auto);
}

.cell {
  width: var(--cell-size);
  height: var(--cell-size);
  border: 1px solid black;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  cursor: pointer;
}

.cell:first-child,
.cell:nth-child(2),
.cell:nth-child(3) {
  border-top: none;
}

.cell:nth-child(3n + 1) {
  border-left: none;
}

.cell:nth-child(3n + 3) {
  border-right: none;
}

.cell:last-child,
.cell:nth-child(8),
.cell:nth-child(7) {
  border-bottom: none;
}

.cell.x,
.cell.circle {
  cursor: not-allowed;
}

.cell.x::before,
.cell.x::after,
.cell.circle::before {
  background-color: black;
}

.board.x .cell:not(.x):not(.circle):hover::before,
.board.x .cell:not(.x):not(.circle):hover::after,
.board.circle .cell:not(.x):not(.circle):hover::before {
  background-color: lightgrey;
}

.cell.x::before,
.cell.x::after,
.board.x .cell:not(.x):not(.circle):hover::before,
.board.x .cell:not(.x):not(.circle):hover::after {
  content: '';
  position: absolute;
  width: calc(var(--mark-size) * 0.15);
  height: var(--mark-size);
}

.cell.x::before,
.board.x .cell:not(.x):not(.circle):hover::before {
  transform: rotate(45deg);
}

.cell.x::after,
.board.x .cell:not(.x):not(.circle):hover::after {
  transform: rotate(-45deg);
}

.cell.circle::before,
.cell.circle::after,
.board.circle .cell:not(.x):not(.circle):hover::before,
.board.circle .cell:not(.x):not(.circle):hover::after {
  content: '';
  position: absolute;
  border-radius: 50%;
}

.cell.circle::before,
.board.circle .cell:not(.x):not(.circle):hover::before {
  width: var(--mark-size);
  height: var(--mark-size);
}

.cell.circle::after,
.board.circle .cell:not(.x):not(.circle):hover::after {
  width: calc(var(--mark-size) * 0.7);
  height: calc(var(--mark-size) * 0.7);
  background-color: white;
}

.winning-message {
  position: fixed;
  top: 15%;
  left: 40%;
  right: 40%;
  background-color: black !important;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
  font-size: 5rem;
  flex-direction: column;
}

.winning-message button {
  font-size: 3rem;
  background-color: white;
  border: 1px solid black;
  padding: 0.25em 0.5em;
  cursor: pointer;
}

.winning-message button:hover {
  background-color: black;
  color: white;
  border-color: white;
}

.winning-message.show {
  display: flex;
}

.hover-x {
  position: relative;
  &:hover::before {
    content: 'X';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: black;
    font-size: 3em;
  }
}

.hover-circle {
  position: relative;
  &:hover::before {
    content: 'O';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: black;
    font-size: 3em;
  }
}

@media (max-width: 800px) {
  h1 {
    font-size: 1.3rem;
  }
  .board {
    height: 65vh;
  }
  .winning-message {
    top: 20%;
    left: 20%;
    right: 20%;
  }
}
@media (max-width: 500px) {
  h1 {
    padding-top: 150px;
  }
}
</style>
