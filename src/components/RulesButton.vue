<template>
    <div class="rules">
        <button @click="modal = true">RULES</button>
    </div>
    <div class="modal" v-if="modal">
        <div class="modal-content">
            <h1>RULES</h1>
            <img src="../assets/image-rules.svg" alt="Game Rules">
            <button class="cancel"><img src="../assets/icon-close.svg" alt="" @click="modal = false"></button>
        </div>
    </div>
</template>

<script>
export default {
    name:'RulesButton',
    data(){
        return{
            modal:false,
        }
    },
}
</script>

<style scoped>

    .rules>button{
        border:2px solid rgb(204, 201, 201);
        color:#fff;
        background: transparent;
        font-size: 1.1rem;
        padding:0.8rem 2rem;
        border-radius: 0.4rem;
    }

    .rules>button:hover{
        background-color: #fff;
        color:hsl(237, 49%, 15%);
        border:2px solid #fff;
    }

    .modal{
       position: fixed;
        top:0;
        left: 0;
        width:100%;
        height: 100vh;
        z-index: 200;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .modal-content{
        background-color: #fff;
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        width:100%;
        height: 100%;
    }

    .modal-content h1{
        color:hsl(229, 25%, 31%)
    }
    
    .cancel{
        border:none;
        background-color: transparent;
    }
    @media (min-width:1025px){
        .rules{
            position: absolute;
            bottom:5rem;
            right:5rem;
        }

        .modal-content{
            width:400px;
            height:400px;
            border-radius: 1rem;
            padding:2rem;
            position: relative;
            justify-content: space-between;
        }

        .modal-content h1{
            align-self: flex-start;
        }

        .cancel{
            position: absolute;
            top: 2.5rem;
            right:2rem;
        }
    }
</style>