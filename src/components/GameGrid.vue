<template>
  <div>
    <div class="container">
      <!-- <GridSquare /> -->
      <div class="grid">
        <div
          @click="squareClicked(square)"
          v-for="square in playsquares"
          :key="square.id"
          class="grid-item"
        >
{{ square.playOption }}
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
  methods: {
    squareClicked(sq) {
        console.log(this.playsquares)
      console.log("clicked", sq);
      this.$emit('clicked-square', sq);
    if (this.choice === 'X') {
    sq.playOption = 'X';
    }else if (this.choice === '0'){
        sq.playOption = '0';
    }
    },
  },
  data() {
    return { 
playOption: null
    

    };
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
}

.grid-item:hover {
  background: salmon;
}
</style>
