<template>
  <h1>Reaction Timer</h1>
  <p>A typical human reaction time is 200 to 300 milliseconds.</p>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score" />
</template>



<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue' 

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return { 
      isPlaying: false,
      delay: null, //amount of time before the block appear on the screen
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000 // 2000 ms base time
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) { //auto passed variables when calling the custom event "close"
      this.score = reactionTime
      this.isPlaying = false
      this.showResults=true
    }
  }
}
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
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 16px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
