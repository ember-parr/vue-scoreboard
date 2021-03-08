<template>
  <!-- <h3>{{ message ? "Begin Play... " : message }}</h3> -->
  <div>
    <h3>{{ message }}</h3>
  </div>
</template>

<script>
export default {
  props: ["teams", "winner"],
  data() {
    return {
      currentWinner: this.winner
    };
  },
  methods: {
    createMessage() {
      let plural = true;
      let pointDifference = 0;
      let [teamA, teamB] = this.teams;

      if (teamA.score > teamB.score) {
        pointDifference = teamA.score - teamB.score;
        if (pointDifference === 1) {
            plural = false;
        }
        return `${this.winner} are winning by ${pointDifference} ${
          plural ? "points" : "point"
        } `;
      } else if (teamA.score < teamB.score) {
        pointDifference = teamB.score - teamA.score;
        if (pointDifference === 1) {
            plural = false;
        }
        return `${this.winner} are winning by ${pointDifference} ${
          plural ? "points" : "point"
        } `;
      } else if (teamA.score === 0 && teamB.score === 0) {
        return "start playing!";
      } else if (teamA.score === teamB.score) {
        return "TIE GAME";
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
