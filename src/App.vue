<template>
  <div id="app">
    <div v-if="winner === 'X'" class="overlay">
      <div>
        Player X has won!
        <img src="https://media.giphy.com/media/zfYpmAfrcVOAE/giphy.gif" />
      </div>
      <!-- <div>Player 0 has won!</div>
      <div>It's a draw!</div> -->
    </div>
      <div v-if="winner === '0'" class="overlay">
      <div>
        Player 0 has won!
        <img src="https://media2.giphy.com/media/fedlFucnJ7VPa/giphy.gif" />
      </div>
      <!-- <div>Player 0 has won!</div>
      <div>It's a draw!</div> -->
    </div>
    <PlayerChoice
      @player-choice="choosePlayer"
      @chosen="isChosen"
      :reset="hasReset"
    />
    <GameGrid
      :playsquares="squares"
      :choice="playerOption"
      @clicked-square="clickedOn"
      @reset="resetChoice"
      @winner="establishWinner"
    />
  </div>
</template>

<script>
import GameGrid from "./components/GameGrid";
import PlayerChoice from "./components/PlayerChoice";

export default {
  name: "App",
  components: {
    GameGrid,
    PlayerChoice,
  },
  data() {
    return {
      playerOption: null,
      hasChosen: false,
      hasReset: false,
      winner: null,
      squares: [
        {
          name: "1",
          clicked: null,
          isWon: false,
        },
        {
          name: "2",
          clicked: null,
          isWon: false,
        },
        {
          name: "3",
          clicked: null,
          isWon: false,
        },
        {
          name: "4",
          clicked: null,
          isWon: false,
        },
        {
          name: "5",
          clicked: null,
          isWon: false,
        },
        {
          name: "6",
          clicked: null,
          isWon: false,
        },
        {
          name: "7",
          clicked: null,
          isWon: false,
        },
        {
          name: "8",
          clicked: null,
          isWon: false,
        },
        {
          name: "9",
          clicked: null,
          isWon: false,
        },
      ],
    };
  },
  methods: {
    choosePlayer(opt) {
      this.playerOption = opt;
    },
    isChosen(option) {
      this.hasChosen = option;
    },
    clickedOn() {
      if (this.playerOption === "X") {
        this.playerOption = "0";
      } else {
        this.playerOption = "X";
      }
    },
    resetChoice() {
      this.playerOption = null;
      this.hasChosen = false;
      this.hasReset = true;
      this.winner = null;
      this.squares.forEach((value) => {
        value.clicked = null;
        value.isWon = false;
      });
    },
    establishWinner(win) {
      this.winner = win;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.result-window {
  margin-top: 20px;
  border: 1px solid orchid;
  padding: 5px;
}
</style>
