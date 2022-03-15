<template>
  <h1>How fast can you catch me?</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <div v-if="isPlaying">
    <BlockModal :delay="delay" @endGame="endGame"/> 
  </div>
  <div v-if="end">
    <Result :score="score"/>
  </div>
</template>

<script>

import BlockModal from "./components/BlockModal.vue";
import Result from "./components/Result.vue";
export default {
  name: 'App',
  data(){
    return{
      isPlaying: false,
      delay: null,
      end: false
    }
  },
  components: {
    BlockModal,
    Result
  },
  methods: {
    start(){
      this.isPlaying=true;
      this.delay=2000+Math.random()*5000;
    },
    endGame(score){
      this.score = score;
      this.isPlaying=false;
      this.end=true
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
</style>
