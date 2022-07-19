<template>
    <div class="choice" :class="choice.name">
        <button :id="index" @click="handleChoice($event.currentTarget.id)">
            <img :src="require('../assets/' + choice.img)" alt="">
        </button>
    </div>
</template>

<script>
export default{
    name:'ChoiceButton',
    props:['choice', 'index'],
    inject:['handleChoice'],
}
</script>

<style scoped>
.choice> button{
    border-radius: 50%;
    width:100px;
    height:100px;
    border: 1rem solid transparent;
    box-sizing: content-box;
    background-origin: border-box;
    background-clip: content-box, border-box;
    position: relative;
    z-index: 100;
}



.choice> button:hover{
    transform: scale(1.1);
}


.paper>button{
    background-image: linear-gradient(white, white), 
                    linear-gradient(to right, hsl(230, 89%, 62%) ,hsl(230, 89%, 65%));
    box-shadow: 0 8px 0 0 hsl(230, 80%, 51%), inset 0 6px 0 0 hsl(0, 1%, 79%);
}

.scissors>button{
    background-image: linear-gradient(white, white), 
                    linear-gradient(to right,hsl(39, 89%, 49%) , hsl(40, 84%, 53%));
    box-shadow: 0 8px 0 0 hsl(39, 97%, 35%), inset 0 6px 0 0 hsl(0, 1%, 79%);
}

.rock>button{
    background-image: linear-gradient(white, white), 
                    linear-gradient(to right,hsl(349, 71%, 52%), hsl(349, 70%, 56%));
    box-shadow: 0 8px 0 0 hsl(349, 93%, 28%), inset 0 6px 0 0 hsl(0, 1%, 79%); 
}

@media (min-width:1025px){
    .choice> button{
        width:130px;
        height: 130px;
        border-width:1.5rem;
    }
}

</style>