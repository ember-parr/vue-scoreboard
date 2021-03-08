<template>
  <h3>{{ message ? "Begin Play... " : message }}</h3>
</template>

<script>
import { teams } from "../data.js";
export default {
  methods: {
    createMessage() {
      let plural = true;
      let pointDifference = 0;
      let [teamA, teamB] = teams;

      if (teamA.score > teamB.score) {
        pointDifference = teamA.score - teamB.score;
        return `${teamA.name}'s is winning by ${pointDifference} ${
          plural ? "points" : "point"
        } `;
      } else if (teamA.score < teamB.score) {
        pointDifference = teamB.score - teamA.score;
        return plural;
      } else if (teamA.score === teamB.score) {
        return "TIE GAME!";
      }
    }
  },
  computed: {
    message() {
      return this.createMessage();
    }
  }
};
</script>

<style scoped>
h3 {
  padding: 25px 0px;
  background: darkgray;
  width: 100%;
}
</style>
