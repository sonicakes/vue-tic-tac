<template>
  <div id="app">
    <PlayerChoice @player-choice="choosePlayer" @chosen="isChosen" />
    <p>{{ playerOption}}</p>
    <p>{{ hasChosen }}</p>
    <GameGrid/>
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
      // squares: ['1', '2', '3', '4', '5', '6', '7', '8', '9']
      squares: []
    };
  },
  methods: {
    choosePlayer(opt) {
      this.playerOption = opt;
    },
    isChosen(option) {
      this.hasChosen = option;
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
</style>
