<template>  
    <h1>How fast can you catch me?</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <div class="container">
        <div class="position" :style="{top: top, left: left}" v-if="isPlaying">
            <Block :delay="delay" @endGame="endGame"/>
        </div>
        <div v-if="showResult">
            <Result :score="score"/>
        </div>
    </div>
</template>

<script>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"

export default {
    name: 'App',
    components:{
        Block,
        Result,
    },
    data(){
        return{
            isPlaying: false,//button click and start game
            delay: null,//random number
            score: 0,
            top: null,
            left: null,
            color: "red",
            position: false,
            showResult: false,//Result.vue
        }
    },
    methods:{
        start(){
            this.isPlaying=true;
            this.delay=2000+Math.random()*5000;
            this.top=Math.random()*262 + "px";
            this.left=Math.random()*380 + "px";
            //console.log(this.top);
            this.showResult=false;
        },
        endGame(score){
            this.score = score;
            this.isPlaying=false;
            this.showResult=true;
        }
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
.container{
    width: 500px;
    height: 300px;
    margin: 20px auto;
    border: 2px solid black;
}
button{
    padding: 10px 30px;
    background: rgb(0, 201, 201);
}
.position{
    position: relative;
}
</style>
