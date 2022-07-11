<template>
  <div class="container">
    <ScoreBoard/>
    <userChoice/>
    <RulesButton/>
  </div>
</template>

<script>
import ScoreBoard from './components/ScoreBoard.vue';
import userChoice from './components/userChoice.vue';
import RulesButton from './components/RulesButton.vue';
export default {
  name: 'App',
  components: {
    ScoreBoard, userChoice, RulesButton
  },
  methods:{
    showRules(){
      console.log("show rules")
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
  gap:4rem;
  align-items: center;
}

@media (min-width:1025px){
  .container{
    width:60%;
    max-width: 800px;
    gap:5rem;
  }
}

</style>
