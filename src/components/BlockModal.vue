<template>
    <div v-if="showBlock">
        <div class="block" @click="stopTimer">Click me {{delay}}</div>
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return{
            showBlock: false,
            score:0,
            timer:null
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock=true;
            this.startTimer();
        },this.delay);
    },
    methods:{
        startTimer(){
            this.timer=setInterval(()=>{
                this.score+=50;
            },50);
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit('endGame', this.score);
        }
        
    }
}

</script>

<style>
.block{
    width: 400px;
    height: 200px;
    margin:20px auto;
    padding: 20px;
    background-color: aqua;
}
</style>