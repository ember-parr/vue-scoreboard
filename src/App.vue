<template>
  <div id="app">
    <img alt="Rover logo" src="./assets/rover.png" class="headerImg" />
    <matchup-title  />
  </div>
</template>

<script>
import MatchupTitle from "./components/MatchupTitle.vue";
export default {
  name: "App",
  components: {
    MatchupTitle
  },
  
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-image: url(assets/background.jpg);
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  max-width: 100%;
  height: auto;
}
.headerImg {
  width: 20%;
  height: auto;
  padding: 30px;
}
</style>
