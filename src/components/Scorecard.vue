<template>
  <div>
    <h3>{{ team.name }}</h3>
    <h2>{{ team.score }}</h2>
    <button class="minusBtn" :disabled="team.score === 0" @click="minusPoint">
      -
    </button>
    <button class="plusBtn" @click="plusPoint">+</button>
  </div>
</template>

<script>
export default {
  props: ["team"],
  methods: {
    minusPoint() {
      this.$emit("minus-point", this.team);
    },
    plusPoint() {
      this.$emit("plus-point", this.team);
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
  padding: 10px;
  border-radius: 10px;
  color: white;
  font-size: 2rem;
  border: none;
  width: 50px;
}
.minusBtn {
  background-color: #2f5476;
  margin-right: 20px;
}
.plusBtn {
  background-color: #6c94ac;
}
</style>
