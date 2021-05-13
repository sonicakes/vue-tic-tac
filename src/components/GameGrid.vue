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
  </div>
</template>

<script>
// import GridSquare from "./GridSquare";

export default {
  components: {
    // GridSquare,
  },
  props: ["playsquares", "choice"],

  data() {
    return {
      choiceOpt: null,
    };
  },
  //   mounted() {
  // this.choiceOpt = this.choice;
  //       },
  computed: {},

  methods: {
    squareClicked(sq, idx) {
      console.log("beginning", this.choice);
      console.log(this.playsquares);
      console.log("clicked", sq.name);
      this.$emit("clicked-square", sq);

      if (this.choice === "0") {
        this.playsquares[idx].clicked = "0";
      } else if (this.choice === "X") {
        this.playsquares[idx].clicked = "X";
      } else {
        alert("you have to pick sides first");
      }

      console.log(this.choice);
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

.symbol {
  position: absolute;
  height: 50px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
