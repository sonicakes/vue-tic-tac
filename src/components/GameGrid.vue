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
          :class="{ winner: square.isWon }"
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
      isWon: false,
    };
  },
  emits: ["clicked-square", "reset", "winner"],

  methods: {
    squareClicked(sq, idx) {
      this.$emit("clicked-square");

      if (this.choice === "0") {
        this.playsquares[idx].clicked = "0";
      } else if (this.choice === "X") {
        this.playsquares[idx].clicked = "X";
      } else {
        alert("you have to pick sides first");
      }
      this.determineWinner();
    },
    determineWinner() {
      //X combos

      //0, 4, 8 diagonal
      if (
        this.playsquares[0].clicked &&
        this.playsquares[4].clicked &&
        this.playsquares[8].clicked === "X"
      ) {
        this.winner = "X";
        this.playsquares[0].isWon = true;
        this.playsquares[4].isWon = true;
        this.playsquares[8].isWon = true;
        this.$emit("winner", this.winner);
      }
      //0, 1, 2 horizontal
       if (
        this.playsquares[0].clicked &&
        this.playsquares[1].clicked &&
        this.playsquares[2].clicked === "X"
      ) {
        this.winner = "X";
        this.playsquares[0].isWon = true;
        this.playsquares[1].isWon = true;
        this.playsquares[2].isWon = true;
        this.$emit("winner", this.winner);
      }
      //2,4,6 diagonal
        if (
        this.playsquares[2].clicked &&
        this.playsquares[4].clicked &&
        this.playsquares[6].clicked === "X"
      ) {
        this.winner = "X";
        this.playsquares[2].isWon = true;
        this.playsquares[4].isWon = true;
        this.playsquares[6].isWon = true;
        this.$emit("winner", this.winner);
      }
       //3,4,5 horizontal
        if (
        this.playsquares[3].clicked &&
        this.playsquares[4].clicked &&
        this.playsquares[5].clicked === "X"
      ) {
        this.winner = "X";
        this.playsquares[3].isWon = true;
        this.playsquares[4].isWon = true;
        this.playsquares[5].isWon = true;
        this.$emit("winner", this.winner);
      }
          //6,7,8 horizontal
        if (
        this.playsquares[6].clicked &&
        this.playsquares[7].clicked &&
        this.playsquares[8].clicked === "X"
      ) {
        this.winner = "X";
        this.playsquares[6].isWon = true;
        this.playsquares[7].isWon = true;
        this.playsquares[8].isWon = true;
        this.$emit("winner", this.winner);
      }
          //0,3,6 vertical
        if (
        this.playsquares[0].clicked &&
        this.playsquares[3].clicked &&
        this.playsquares[6].clicked === "X"
      ) {
        this.winner = "X";
        this.playsquares[0].isWon = true;
        this.playsquares[3].isWon = true;
        this.playsquares[6].isWon = true;
        this.$emit("winner", this.winner);
      }
              //1,4,7 vertical
        if (
        this.playsquares[1].clicked &&
        this.playsquares[4].clicked &&
        this.playsquares[7].clicked === "X"
      ) {
        this.winner = "X";
        this.playsquares[1].isWon = true;
        this.playsquares[4].isWon = true;
        this.playsquares[7].isWon = true;
        this.$emit("winner", this.winner);
      }
                //2,5,8 vertical
        if (
        this.playsquares[2].clicked &&
        this.playsquares[5].clicked &&
        this.playsquares[8].clicked === "X"
      ) {
        this.winner = "X";
        this.playsquares[2].isWon = true;
        this.playsquares[5].isWon = true;
        this.playsquares[8].isWon = true;
        this.$emit("winner", this.winner);
      }

      //0 combos

            //0, 4, 8 diagonal
      if (
        this.playsquares[0].clicked &&
        this.playsquares[4].clicked &&
        this.playsquares[8].clicked === "0"
      ) {
        this.winner = "0";
        this.playsquares[0].isWon = true;
        this.playsquares[4].isWon = true;
        this.playsquares[8].isWon = true;
        this.$emit("winner", this.winner);
      }
      //0, 1, 2 horizontal
       if (
        this.playsquares[0].clicked &&
        this.playsquares[1].clicked &&
        this.playsquares[2].clicked === "0"
      ) {
        this.winner = "0";
        this.playsquares[0].isWon = true;
        this.playsquares[1].isWon = true;
        this.playsquares[2].isWon = true;
        this.$emit("winner", this.winner);
      }
      //2,4,6 diagonal
        if (
        this.playsquares[2].clicked &&
        this.playsquares[4].clicked &&
        this.playsquares[6].clicked === "0"
      ) {
        this.winner = "0";
        this.playsquares[2].isWon = true;
        this.playsquares[4].isWon = true;
        this.playsquares[6].isWon = true;
        this.$emit("winner", this.winner);
      }
       //3,4,5 horizontal
        if (
        this.playsquares[3].clicked &&
        this.playsquares[4].clicked &&
        this.playsquares[5].clicked === "0"
      ) {
        this.winner = "0";
        this.playsquares[3].isWon = true;
        this.playsquares[4].isWon = true;
        this.playsquares[5].isWon = true;
        this.$emit("winner", this.winner);
      }
          //6,7,8 horizontal
        if (
        this.playsquares[6].clicked &&
        this.playsquares[7].clicked &&
        this.playsquares[8].clicked === "0"
      ) {
        this.winner = "0";
        this.playsquares[6].isWon = true;
        this.playsquares[7].isWon = true;
        this.playsquares[8].isWon = true;
        this.$emit("winner", this.winner);
      }
          //0,3,6 vertical
        if (
        this.playsquares[0].clicked &&
        this.playsquares[3].clicked &&
        this.playsquares[6].clicked === "0"
      ) {
        this.winner = "0";
        this.playsquares[0].isWon = true;
        this.playsquares[3].isWon = true;
        this.playsquares[6].isWon = true;
        this.$emit("winner", this.winner);
      }
              //1,4,7 vertical
        if (
        this.playsquares[1].clicked &&
        this.playsquares[4].clicked &&
        this.playsquares[7].clicked === "0"
      ) {
        this.winner = "0";
        this.playsquares[1].isWon = true;
        this.playsquares[4].isWon = true;
        this.playsquares[7].isWon = true;
        this.$emit("winner", this.winner);
      }
                //2,5,8 vertical
        if (
        this.playsquares[2].clicked &&
        this.playsquares[5].clicked &&
        this.playsquares[8].clicked === "0"
      ) {
        this.winner = "0";
        this.playsquares[2].isWon = true;
        this.playsquares[5].isWon = true;
        this.playsquares[8].isWon = true;
        this.$emit("winner", this.winner);
      }

    },
    resetGame() {
      this.playsquares.forEach((value) => {
        value.clicked = null;
        value.isWon = false;
        this.$emit("reset");
      });
    },
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

.grid-item.winner {
  background: seagreen;
  border-color: orchid;
}

.symbol {
  position: absolute;
  height: 50px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
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
