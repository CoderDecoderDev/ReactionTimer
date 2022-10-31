<template>
  <h1 class="title is-1 py-5">Reaction Timer</h1>
  <p class="">What are your reactions like? A typical human reaction time is 200 to 300 milliseconds. Our tool will test your reaction time and show you the results. </p>
  <p>Please press this button in order to check your reaction time:</p>
  <button @click="start" :disabled="isPlaying" class="button is-success is-medium my-3">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <p v-if="showResult" class="content is-large">Your reaction time is: {{ score }} ms.</p>
</template>

<script>
import Block from "./components/Block.vue"

export default {
  name: 'App',
  components: {Block},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.delay = 1000 + Math.random() * 2000,
      this.isPlaying = true,
      this.showResult = false
    },
    endGame(endScore) {
      this.score = endScore,
      this.isPlaying = false,
      this.showResult = true
    }
  }
}
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


</style>
