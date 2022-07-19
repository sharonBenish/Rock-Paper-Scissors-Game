<template>
    <div class="choices">
        <img class="joint traingle" src="../assets/bg-triangle.svg" alt="">
        <ChoiceButton v-for="(choice, index) in choices" :key="choice.name" :choice='choice' :index = 'index'/>    
    </div>
</template>

<script>
import ChoiceButton from './ChoiceButton.vue'
export default{
    name: "userChoice",
    components: { ChoiceButton },
    props: ["choices"],
    methods: {},
}
</script>

<style scoped>
.choices{
    display:flex;
    flex-wrap: wrap;
    justify-content: space-between;
    gap:50px;
    max-width: 400px;
    position: relative;
}

.choice:last-of-type{
    width:100%;
    text-align: center;
}

.joint{
    position: absolute;
    left:50%;
    bottom:0px;
    transform: translateX(-50%); 

}

@media (min-width:1025px){
    .choices{
        max-width:600px;
        
    }

    .joint{
        top:50%;
        bottom:auto;
        transform: translate(-50%,-50%);
    }
}
</style>