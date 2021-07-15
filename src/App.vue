<template>
  <h1>Reaction Timer Game</h1>
  <button @click="start" :disabled="isPlaying">Start Game</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="scoreShow" :reactionTime="storeReaction"/>
  <a href="https://github.com/jahidNITS" class="dontClick">don't click</a>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block, Results
  },
  data() {
    return {
      isPlaying : false,
      delay : null,
      storeReaction : null,
      scoreShow : false
    }
  },
  methods: {
    start(){
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      this.scoreShow = false
    },
    endGame(reaction){
      this.storeReaction = reaction
      this.isPlaying = false
      this.scoreShow = true
    }
  },
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
button{
  height: 45px;
  padding: 0 30px;
  background: #000;
  font-size: 16px;
  color: #FFF;
  border-radius: 5px;
  border: none;
  outline: none;
  font-weight: 600;
  cursor: pointer;
}
button:disabled,
button[disabled]{
  background-color: rgb(44, 42, 42);
  color: #666666;
}

a.dontClick{
  position: absolute;
  top: 40px;
  left: 50px;
  font-weight: 600;
  text-transform: capitalize;
  font-size: 16px;
  color: #000;
}
</style>
