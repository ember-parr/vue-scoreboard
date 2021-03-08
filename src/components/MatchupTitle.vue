<template>
  <div>
    <h1>Team 1 vs Team 2</h1> <br />
    <p>who's winning?!</p>
    <div v-for="team in teams" :key="team.id" class="pointsBox">
      <scorecard :team="team" />
    </div>
  </div>
</template>

<script>
import { teams } from "../data";
import Scorecard from "./Scorecard.vue";
export default {
  components: { Scorecard },
  data() {
    return {
      teams: [...teams]
    };
  }
};
</script>

<style scoped>
.pointsBox {
    display: flex;
    justify-content: space-around;
    align-content: flex-start;
    width: 100%;
    height: auto;
}
h1 {
    width: 100%;
    color: white;
}
p {
    padding: 25px 0px;
    background: darkgray;
    width: 100%;
}

</style>
