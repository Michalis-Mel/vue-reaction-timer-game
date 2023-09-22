<template>
  <h1>My Reaction Timer Game</h1>
  <button class="playBtn" :disabled="isPlaying" @click="startGame">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  components: { Block, Results },
  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
h1 {
  font-size: 50px;
  margin: 0 auto;
}
.playBtn {
  border: none;
  padding: 10px 20px;
  border-radius: 30px;
  margin: 50px auto 0 auto;
  font-size: 26px;
  cursor: pointer;
  color: #fff;
  background: rgb(22, 187, 41);
}
.playBtn:hover {
  background: rgb(9, 101, 9);
}
.playBtn[disabled] {
  cursor: not-allowed;
  opacity: 0.2;
}
</style>
