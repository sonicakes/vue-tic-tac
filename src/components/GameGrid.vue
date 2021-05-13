<template>
  <div class="container">
    <div class="grid">
      <GridSquare @click="squareClicked('1')"/>
      <GridSquare number="2"/>
      <GridSquare number="3"/>
      <GridSquare number="4"/>
      <GridSquare number="5"/>
      <GridSquare number="6"/>
      <GridSquare number="7"/>
      <GridSquare number="8"/>
      <GridSquare number="9"/>
    </div>
  </div>
</template>

<script>
import GridSquare from "./GridSquare";

export default {
  components: {
    GridSquare,
  },
  methods: {
      squareClicked (num) {
          this.$emit('clicked-square', num);
      }
  }
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
</style>
