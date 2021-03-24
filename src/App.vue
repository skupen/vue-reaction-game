<template>
  <Block @closeBlock="closeModal($event)" v-if="isOpenedBlock"></Block>
  <button v-if="isStartButtonVisible" @click="reactionInterval">Start this shit</button>
  <Result @buttonAgain="playAgain" v-if="isResultVisible" :result="reactionTime" :aResults="results"/>
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
  data(){
    return{
      isOpenedBlock: false,      
      isStartButtonVisible: true,   
      isResultVisible: false,
      randomTimeGenerated: 4,
      reactionTime: Number,
      results: []
    } 
  },

  methods: {
    openModal(){
      this.isOpenedBlock = !this.isOpenedBlock;
    },
    reactionInterval(){
      this.randomTimeGenerated = this.randomTime();
      this.isStartButtonVisible = !this.isStartButtonVisible;
      setTimeout(this.openModal, this.randomTimeGenerated);      
    },
    randomTime(){
      return Math.floor(((Math.random() * 4) + 0.2) * 1000); 
    },
    closeModal(reactionTime){
      this.isOpenedBlock = !this.isOpenedBlock;
      this.reactionTime = reactionTime;
      this.isResultVisible = !this.isResultVisible;
      this.results.push(reactionTime);
    },
    playAgain(){
      this.isOpenedBlock = false;
      this.isStartButtonVisible = true;
      this.isResultVisible = false;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
  justify-items: center;
  height: 100vh;
}
</style>
