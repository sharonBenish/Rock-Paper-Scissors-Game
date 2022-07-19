<template>
  <div class="container">
    <ScoreBoard :score='score'/>
    <userChoice v-if="state == 'start'" :choices='choices'/>
    <PlayMode v-else :selected="selected" :choices="choices" :updateScore='updateScore' @replay="state='start'"/>
    <RulesButton />
  </div>
</template>

<script>
import ScoreBoard from './components/ScoreBoard.vue';
import userChoice from './components/userChoice.vue';
import RulesButton from './components/RulesButton.vue';
import PlayMode from './components/PlayMode.vue';
export default {
  name: 'App',
  components: {
    ScoreBoard,
    userChoice,
    RulesButton,
    PlayMode,
},
  data(){
    return{
      state:'start',
      user:null,
      computer:null,
      score:0,
      choices:[
        {
          name:'paper',
          img:'icon-paper.svg',
        },
        {
          name:'scissors',
          img:'icon-scissors.svg'
        },
        {
          name:'rock',
          img:"icon-rock.svg"
        }
      ],
    }
  },
  methods:{
    makeChoice(target){
      this.user = target;
      this.state='playMode';
    },
    selected(){
      return this.choices[this.user]
    },
    updateScore(operator){
      if(operator== "add"){
        this.score += 1;
      }
      if(operator == "minus"){
        --this.score;
      }
    },

  },
  provide(){
    return{
      handleChoice: this.makeChoice,
      replay: this.updateScore,
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@400;600;700&display=swap');

*{
  margin:0;
  padding:0;
  box-sizing: border-box;
  font-family: 'Barlow Semi Condensed', sans-serif;
}
#app {
  height: 100vh;
  background: radial-gradient(farthest-corner at 50% 0px,hsl(214, 47%, 23%), hsl(237, 49%, 15%));
  overflow-y: hidden;
  
}

.container{
  width:90%;
  max-width: 600px;
  margin: 0 auto;
  padding:2rem 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 100vh;
}

@media (min-width:1025px){
  .container{
    width:60%;
    max-width: 800px;
    gap:5rem;
    justify-content: unset;
  }
}

</style>
