<template>
  <div id="app">
    <PlayerChoice @player-choice="choosePlayer" @chosen="isChosen" />
    <p>{{ playerOption}}</p>
    <p>{{ hasChosen }}</p>
    <GameGrid :playsquares="squares" :choice="playerOption" @clicked-square="clickedOn"/>
    <p>clicked on square # {{ clicked }}</p>
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
      squares: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      clicked: null
    };
  },
  methods: {
    choosePlayer(opt) {
      this.playerOption = opt;
    },
    isChosen(option) {
      this.hasChosen = option;
    },
    clickedOn(sq) {
      this.clicked = sq;
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
