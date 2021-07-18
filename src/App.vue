<template>
  <h1>Reaction - timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <br />
  <Block v-if="isPlaying" :delay="delay" @end="end" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      console.log("start");
      this.isPlaying = true;
      this.showResult = false;
      this.delay = Math.random() * 3000;
    },
    end(reactionTime) {
      console.log("end");
      this.isPlaying = false;
      this.score = reactionTime;
      this.showResult = true;
      console.log("reactionTime: " + reactionTime);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
