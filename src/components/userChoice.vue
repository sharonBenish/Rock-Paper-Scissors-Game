<template>
    <div class="choices">
        <img class="joint traingle" src="../assets/bg-triangle.svg" alt="">
        <div class="choice">
            <button id="paper">
                <img src="../assets/icon-paper.svg" alt="">
             </button>
        </div>
        <div class="choice">
             <button id="scissors">
                <img src="../assets/icon-scissors.svg" alt="">
            </button>
        </div>
        <div class="choice">
            <button id="rock">
                <img src="../assets/icon-rock.svg" alt="">
            </button>
        </div>       
    </div>
</template>

<script>
export default{
    name:'userChoice',
}
</script>

<style scoped>
.choices{
    display:flex;
    flex-wrap: wrap;
    justify-content: space-between;
    position: relative;
    gap:20px;
    max-width: 400px;
}

.choice> button{
    border-radius: 50%;
    width:100px;
    height:100px;
    border: none;
    box-sizing: content-box;
    border: 1.2rem solid transparent;
    background-origin: border-box;
    background-clip: content-box, border-box;
    position: relative;
    z-index: 100;
}

.choice> button:hover{
    transform: scale(1.1);
}
.choice:last-of-type{
    width:100%;
    text-align: center;
}

#paper{
    background-image: linear-gradient(white, white), 
                    linear-gradient(to right, hsl(230, 89%, 62%) ,hsl(230, 89%, 65%));
    box-shadow: 0 8px 0 0 hsl(230, 80%, 51%), inset 0 6px 0 0 hsl(0, 1%, 79%);
}

#scissors{
    background-image: linear-gradient(white, white), 
                    linear-gradient(to right,hsl(39, 89%, 49%) , hsl(40, 84%, 53%));
    box-shadow: 0 8px 0 0 hsl(39, 97%, 35%), inset 0 6px 0 0 hsl(0, 1%, 79%);
}

#rock{
    background-image: linear-gradient(white, white), 
                    linear-gradient(to right,hsl(349, 71%, 52%), hsl(349, 70%, 56%));
    box-shadow: 0 8px 0 0 hsl(349, 93%, 28%), inset 0 6px 0 0 hsl(0, 1%, 79%); 
}

.joint{
    position: absolute;
    left:50%;
    bottom:0px;
    transform: translateX(-50%); 

}

@media (min-width:1025px){
    .choices{
        max-width: 500px;
        gap:40px;
    }
    .choice> button{
        width:130px;
        height: 130px;
        border-width:1.5rem;
    }

    .joint{
        top:50%;
        bottom:auto;
        transform: translate(-50%,-50%);
    }
}
</style>