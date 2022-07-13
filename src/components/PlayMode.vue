<template>
    <div class="game-choices">
        <div class="user-choice">
            <ChoiceButton :choice='selected()'/>
            <p>YOU PICKED</p>
        </div>
        <div class="house-choice">
            <ChoiceButton v-if="choiceVisible" :choice='computerPicked' />
            <div class="empty" v-else></div>
            <p>THE HOUSE PICKED</p>
        </div>
        <div class="result" v-if="choiceVisible">
            <div>
                <h1>{{message}}</h1>
                <button class="replay" @click="$emit('replay')">PLAY AGAIN</button>
            </div>
        </div>
    </div>
</template>

<script>
import ChoiceButton from "./ChoiceButton.vue";
export default{
    name: "PlayMode",
    components: { ChoiceButton },
    props:['selected', 'choices', 'updateScore'],
    mounted(){
        this.randomChoice();
         setTimeout(()=>{
                this.choiceVisible= true;
                this.result();
        }, 1000) 
    },
    data(){
        return {
            choiceVisible:false,
            userPicked: this.selected(),
            computerPicked:null,
            message:"",
        }
    },
    methods:{
        randomChoice(){
            const randomIdx = Math.floor(Math.random() * this.choices.length);
            this.computerPicked= this.choices[randomIdx];
        },

        result(){
            if(this.computerPicked){
                const userChoice = this.userPicked.name;
                const computerChoice = this.computerPicked.name;
                switch(userChoice + computerChoice){
                    case 'paperpaper':
                    case 'rockrock':
                    case 'scissorsscissors':
                        this.message = "DRAW";
                        break;
                    
                    case 'paperrock':
                    case 'rockscissors':
                    case 'scissorspaper':
                        this.message = "YOU WIN";
                        this.updateScore("add");
                        break;
                    case 'paperscissors':
                    case 'rockpaper':
                    case 'scissorsrock':
                        this.message = "YOU LOSE";
                        this.updateScore("minus");
                        break;
                }

            }
        }
    }
    
}
</script>

<style scoped>
.game-choices {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: flex-end;
    width:100%;;
    max-width: 400px;
}

.game-choices > * {
    padding:1rem 0;
}

.game-choices > *:not(:last-of-type){
    pointer-events: none;
}

.game-choices p{
    color:#fff;
    font-weight: 600;
    text-align: center;
    font-size:0.7rem;
    margin-top:1.5rem;
}
.result{
    width:100%;
    display: flex;
    justify-content: center;
}

.result  h1{
    font-size: 3rem;
    color:#fff;
    margin-bottom: 1.3rem;
}

.replay{
    border: none;
    background-color: #fff;
    color:rgb(20, 21, 57);
    border-radius: 0.8rem;
    width:100%;
    padding:1rem 0;
    font-weight: 600;
    font-size: 0.8rem;
}

.replay:hover{
    transform: scale(1.1);
}

.empty{
    width:120px;
    height: 120px;
    border-radius: 50%;
    background-color:#192644;
}

@media (min-width:1025px){

    .empty{
        width:150px;
        height:150px;
    }
}

@media (min-width:1200px){
    .game-choices{
        width:100%;
        justify-content: center;
        gap:5rem;
        max-width: none;
    }
    .result{
        order:1;
        width:auto
    }
    .house-choice{
        order:2
    }
}
</style>