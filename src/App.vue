<template>
  <div >
    <div class="object-center">  
    <h2 class="text-3xl text-center ">Reaction Game</h2>
     <button class="flex mx-auto mt-8 text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg" 
     @click="start" :disabled='isPlaying'>
        Play
    </button>

    </div>
    <Block v-if="isPlaying" :delay="delay" @end = 'endGame' />
 
    <Results v-if="showResults" :score = "score"/>
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: 'App',
  components: {
   Block,
   Results
  },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score:null,
      showResults: false
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() *5000
      this.isPlaying = true
      this.showResults = false
      // console.log(this.delay);
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults= true
    }
  }
}
</script>

<style>

</style>
