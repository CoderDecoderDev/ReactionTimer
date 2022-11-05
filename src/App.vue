<template>
<section class="section m-5">
  <div class="container">
    <div class="columns">
      <div class="column is-half is-offset-one-quarter is-narrow-mobile">
        <h1 class="title is-1 pb-5">Reaction Timer</h1>
        <p class="pb-5 is-size-5">What are your reactions like? Are you as fast as a bullet or as slow as a snail? A typical human reaction time is 200 to 300 milliseconds. 
          Our tool will test your reaction time and show you the results.<br>        
          In order to start playing the game, please press the green button below.
          When you see the green box on the screen (below the button), click on it as fast as possible.
        </p>
        <p class="is-size-4 has-text-weight-bold has-background-success-light">Please press this button in order to start playing the game:</p>
        <button @click="start" :disabled="isPlaying" class="button is-success is-medium m-5">Play</button>
        <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
        <Results v-if="showResult" :score="score" />
      </div>
    </div>      
  </div>
</section>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',
  components: { Block, Results },
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
  margin: auto;
  padding: auto;
  width: auto;
  font-weight: 500;
}
</style>
