<template>
  <h1>NINJA Reaction Timer</h1>
  <button  @click="start" :disabled="isPlaying">Play</button>
  <the-block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <the-results v-if="showResult" :score="score"/>
  
 
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TheBlock from './components/TheBlock.vue'
import TheResults from './components/TheResults.vue'
export default {
  name: 'App',
  components: {
    TheBlock,
    TheResults
    // HelloWorld
  },
  data() {
    return {
      isPlaying:false,
      delay:null,
      score:null,
      showResult: false,
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying=true;
      this.showResult=false
    },
    endGame(reactionTime){
      this.score=reactionTime,
      this.isPlaying=false,
      this.showResult=true
    }
  },
}
</script>

<style >
template{
  background-color: cornsilk;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 300px;
}
button{
  background: darkblue;
  padding: 10px 40px;
  border-radius: 5px;
  border: none;
  color: white;
  font-size: larger;
  font-weight: bold;
  letter-spacing: 2px;
  cursor: pointer;
}
button:disabled {
  opacity: 0.2;
  cursor: not-allowed;
  /* background-color: rgb(157, 157, 238); */
}

</style>
