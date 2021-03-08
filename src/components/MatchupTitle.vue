<template>
  <div>
    <h1>
      <span :class="{ winner: teams[0].winner }">{{ teams[0].name }} </span>
      vs.
      <span :class="{ winner: teams[1].winner }">{{ teams[1].name }} </span>
    </h1>
    <br />
    <message />
    <div v-for="team in teams" :key="team.id" class="pointsBox">
      <scorecard
        :key="team.id"
        :team="team"
        @plus-point="addPoint"
        @minus-point="minusPoint"
      />
    </div>
  </div>
</template>

<script>
import { teams } from "../data";
import Scorecard from "./Scorecard.vue";
import Message from "./Message.vue";
export default {
  components: { Scorecard, Message },
  data() {
    return {
      teams: [...teams]
    };
  },
  methods: {
    getRank() {
      const [teamA, teamB] = this.teams;
      if (teamA.score === teamB.score) {
        teamA.winner = false;
        teamB.winner = false;
        console.log("team a winning");
      } else if (teamA.score > teamB.score) {
        teamA.winner = true;
        teamB.winner = false;
      } else {
        teamB.winner = true;
        teamA.winner = false;
      }
    },
    addPoint(team) {
      ++team.score;
      this.getRank();
    },
    minusPoint(team) {
      --team.score;
      this.getRank();
    }
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
.winner {
  color: #518abc;
}
</style>
