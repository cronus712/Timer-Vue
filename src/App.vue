<template>
<h1>Reaction timer </h1>
<button @click="start" :disabled="isPlaying"> Play </button>
<!--
  :binding for dynamic values and binding for static
-->
<Block v-if="isPlaying" :delay = "delay" @end = "endGame">
  
</Block>

<Result v-if="showResult" :score = "score">

</Result>

</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,
    Result
  },

  
  data() {
    return {
      isPlaying:false ,
      delay: null,
      score: null,
      showResult: false

    }
  },

  methods: {
   start() {
   this.delay = 2000 + Math.random() * 5000
   this.isPlaying = true 
   this.score = null
   this.showResult = false
   } ,

   endGame(reactionTime) {
    this.score = reactionTime
    this.isPlaying = false
    this.showResult = true
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
