<template>
    <div class="Block" v-if="showBlock" @click="stopTimer">click here</div>
</template>

<script>
export default {
    props:["delay"],
    data(){
        return{
            showBlock: false,
            score: 0,
            timer: null
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock=true;//update
            this.startTimer();//start counting score
        }, this.delay);
    },
    methods:{
        startTimer(){
            this.timer=setInterval(()=>{
                this.score+=50;
            }, 50);//add 50 score in every 50milisecond
        },
        stopTimer(){
            clearInterval(this.timer);//stop counting
            this.$emit("endGame", this.score);//send score to app.vue
        }
    }
}
</script>

<style>
    .Block{
        width: 100px;
        background: aqua;
        padding: 10px 10px;
    }
</style>