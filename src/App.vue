<template>
  <div id="app">
    <div class="overlay" v-if="winner === 'X'">
      <a class="cancel" href="#"></a>
      <div class="modal">
        <h2>Player X has won!</h2>
        <div class="content">
          <img src="https://media.giphy.com/media/zfYpmAfrcVOAE/giphy.gif" />
          <p>Click 'refresh' button below to start again</p>
        </div>
      </div>
    </div>

    <div class="overlay" v-if="winner === '0'">
      <a class="cancel" href="#"></a>
      <div class="modal">
        <h2>Player 0 has won!</h2>
        <div class="content">
          <img src="https://media2.giphy.com/media/fedlFucnJ7VPa/giphy.gif" />
          <p>Click 'refresh' button below to start again</p>
        </div>
      </div>
    </div>

    <div class="overlay" v-if="winner === 'draw'">
      <a class="cancel" href="#"></a>
      <div class="modal">
        <h2>It's a draw</h2>
        <div class="content">
          <img src="https://media4.giphy.com/media/30swyC5E1ktVe/giphy.gif" />
          <p>Click 'refresh' button below to start again</p>
        </div>
      </div>
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

.modal {
  margin: 100px auto;
  padding: 20px;
  background: #fff;
  border: 1px solid #666;
  border-radius: 6px;
  box-shadow: 0 0 50px rgba(0, 0, 0, 0.5);
  position: relative;
}

.modal h2 {
  margin-top: 0;
}

.modal .content {
  max-height: 400px;
  overflow: auto;
}

.modal p {
  margin: 0 0 1em;
  text-align: center;
}

.modal p:last-child {
  margin: 0;
}

.overlay {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: 999;
}

.overlay .cancel {
  position: absolute;
  width: 100%;
  height: 100%;
  cursor: default;
}
</style>
