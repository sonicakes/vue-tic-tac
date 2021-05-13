<template>
  <div id="app">
    <PlayerChoice @player-choice="choosePlayer" @chosen="isChosen" />
    <p>{{ playerOption }}</p>
    <p>{{ hasChosen }}</p>
    <GameGrid
      :playsquares="squares"
      :choice="playerOption"
      @clicked-square="clickedOn"
      @reset="resetChoice"
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
      squares: [
        {
          name: "1",
          clicked: null,
        },
        {
          name: "2",
          clicked: null,
        },
        {
          name: "3",
          clicked: null,
        },
        {
          name: "4",
          clicked: null,
        },
        {
          name: "5",
          clicked: null,
        },
        {
          name: "6",
          clicked: null,
        },
        {
          name: "7",
          clicked: null,
        },
        {
          name: "8",
          clicked: null,
        },
        {
          name: "9",
          clicked: null,
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
      console.log("this is getting called");
    },
    resetChoice() {
      this.playerOption = null;
      this.hasChosen = false;
    }
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
</style>
