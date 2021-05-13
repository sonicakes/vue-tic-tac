<template>
  <div>
    <div class="container">
      <!-- <GridSquare /> -->
      <div class="grid">
        <div
          @click="squareClicked(square, index)"
          v-for="(square, index) in playsquares"
          :key="square.id"
          class="grid-item"
        >
          name:{{ square.name }} <br />index:{{ index }}
          <span v-if="square.clicked === 'X'">
            <img class="symbol" src="../assets/cross.png" />
          </span>
          <span v-if="square.clicked === '0'">
            <img class="symbol" src="../assets/0.png" />
          </span>
        </div>
      </div>
    </div>
    <div class="result-window">
      <div>Player X has won!</div>
      <div>Player 0 has won!</div>
      <div>It's a draw!</div>
    </div>
    <div class="button-reset" @click="resetGame">Start again</div>
  </div>
</template>

<script>

export default {
  components: {},
  props: ["playsquares", "choice"],

  data() {
    return {
      winner: null,
    };
  },
  emits: ["clicked-square", "reset"],

  methods: {
    squareClicked(sq, idx) {
      console.log("beginning", this.choice);
      console.log(this.playsquares);
      console.log("clicked", sq.name);
      this.$emit("clicked-square");

      if (this.choice === "0") {
        this.playsquares[idx].clicked = "0";
      } else if (this.choice === "X") {
        this.playsquares[idx].clicked = "X";
      } else {
        alert("you have to pick sides first");
      }

      console.log(this.choice);
    },
    resetGame() {
    this.playsquares.forEach((value, index) => {
    value.clicked = null;
    console.log(value);
    console.log(index);
    this.$emit('reset');
});
    }
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  row-gap: 20px;
  column-gap: 20px;
}

.grid-item {
  width: 150px;
  height: 150px;
  background: lightblue;
  border: 1px solid seagreen;
  cursor: pointer;
  position: relative;
}

.grid-item:hover {
  background: salmon;
}

.symbol {
  position: absolute;
  height: 50px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.result-window {
  margin-top: 20px;
  border: 1px solid orchid;
  padding: 5px;
}

.button-reset {
  background: seagreen;
  width: 100px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  color: #fff;
  margin-top: 20px;
}

.button-reset:hover {
  background: lightblue;
  color: #000;
}
</style>
