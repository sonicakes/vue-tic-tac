<template
  ><div>
    <h2>Choose to be X or 0</h2>
    <p v-if="chosen && option != null">
      You have chosen <span class="chosen">{{ playerChoice }} </span>
    </p>
    <div class="choice-bar">
      <div
        class="button-choice"
        @click="chooseOption('X')"
        :class="{ selected: isChosen('X') }"
      >
        X
      </div>
      <div
        class="button-choice"
        @click="chooseOption('0')"
        :class="{ selected: isChosen('0') }"
      >
        0
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      playerChoice: null,
      chosen: false,
    };
  },
  emits: ["player-choice", "chosen"],
  props: ["reset", "option"],
  methods: {
    isChosen(clicked) {
      if (this.option != null) {
        return this.playerChoice === clicked;
      }
    },
    chooseOption(opt) {
      this.playerChoice = opt;
      this.chosen = true;
      this.$emit("player-choice", opt);
      this.$emit("chosen", this.chosen);
    },
  },
};
</script>

<style scoped>
.choice-bar {
  display: flex;
  justify-content: center;
  align-items: center;
}
.button-choice {
  cursor: pointer;
  width: 50px;
  height: 50px;
  border: 1px solid lightblue;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
  margin-right: 10px;
  font-weight: 700;
}

.button-choice:hover {
  background: seagreen;
  color: white;
}

.button-choice.selected {
  background: seagreen;
  border-color: salmon;
  color: white;
}

.chosen {
  font-weight: 700;
  color: seagreen;
}
</style>
