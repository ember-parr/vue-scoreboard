<template>
  <div>
    <h3>{{ team.name }}</h3>
    <h2>{{ team.score }}</h2>
    <button class="minusBtn">-</button> <button class="plusBtn">+</button>
  </div>
</template>

<script>
export default {
  props: ["team"],
  methods: {
    handlePlusClick() {
      this.$emit("addPoint", this.team);
    }
  },
  computed: {
    score() {
      return this.team.score;
    }
  }
};
</script>

<style scoped>
div {
  color: white;
  border: 4px solid white;
  padding: 10px;
  margin: 15px;
  width: 20%;
  background-color: rgb(211, 211, 211, 0.4);
  flex: 0.4;
}
button {
    padding: 15px;
    border-radius: 10px;
}
.minusBtn {
    background-color: maroon;
}
.plusBtn {
    background-color: forestgreen;
}
</style>
