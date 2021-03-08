<template>
  <div>
    <h1>
      <span :class="{ winner: teamAWinning }">{{ teams[0].name }} </span>
      vs.
      <span :class="{ winner: teamBWinning }">{{ teams[1].name }} </span>
    </h1>
    <br />
    <message :teams="teams" :winner="winner" :pointsDifference="0" />
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
      teams: [...teams],
      teamAWinning: false,
      teamBWinning: false,
      winner: ""
    };
  },
  methods: {
    getRank() {
      const [teamA, teamB] = this.teams;
      if (teamA.score === teamB.score) {
        this.teamAWinning = false;
        this.teamBWinning = false;
        this.winner = "tie";
      } else if (teamA.score > teamB.score) {
        this.teamAWinning = true;
        this.teamBWinning = false;
        this.winner = teamA.name;
      } else {
        this.teamBWinning = true;
        this.teamAWinning = false;
        this.winner = teamB.name;
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
