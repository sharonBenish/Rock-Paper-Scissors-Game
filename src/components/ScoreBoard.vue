<template>
    <div id="score-board">
        <div class="game-name">
            <img src="../assets/logo.svg" alt="">
        </div>
        <div class="score">
            <div>score<span>12</span></div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ScoreBoard',
}
</script>

<style scoped>
#score-board{
    border:2.5px solid hsl(217, 16%, 45%);
    border-radius: 1rem;
    display: flex;
    justify-content: space-between;
    padding:1rem;
    align-items: center;
    max-height: 100px;
    width:100%;
}
.game-name{
    height:60px;
}
.game-name>img{
    width:100%;
    height:100%;
    object-fit: cover;
}
.score{
    padding:0.6rem;
    text-align: center;
    font-size: 0.8rem;
    text-transform: uppercase;
    color:hsl(229, 64%, 46%);
    background-color: #fff;
    border-radius: 0.5rem;
    width:100px;
    height:80px ;
}
.score span{
    color:hsl(229, 25%, 31%);
    display: block;
    font-size: 2.5rem;
    font-weight: 700; 
}

@media (min-width:1025px){
    #score-board{
        max-height:200px;
    }
}
</style>