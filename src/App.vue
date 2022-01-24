<template>
  <h2>How fast can you catch me?</h2>
  <button @click="start" :disabled="isPlaying">Play</button>
  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame"></Block>
  </div>
  <div v-if="end">
    <Result :score="score"></Result>
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: 'App',
  components : {
    Block,
    Result
  },
  data(){
    return {
      isPlaying : false,
      delay : null,
      score : 0,
      end : false
    }
  },
  methods : {
    start(){
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
    },
    endGame(score){
      this.score = score;
      this.isPlaying = false;
      this.end = true;
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
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background-color: rgb(231, 226, 208);
}
</style>
