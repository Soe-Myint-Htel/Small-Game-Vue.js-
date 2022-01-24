<template>
  <p class="block" v-if="showBlock" @click="stopTimer">click here</p>
</template>

<script>
export default {
    props : ['delay'],
    data(){
        return {
            showBlock : false,
            score : 0,
            timer : null,
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock = true;
            this.startTimer();
        },this.delay);
    },
    methods : {
        startTimer(){
            this.timer = setInterval(() => {
                this.score += 50; 
            }, 50);
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit("endGame", this.score);
        }
    }
}
</script>

<style>
.block {
    width: 400px;
    height: 200px;
    background-color: blueviolet;
    border: none;
    border-radius: 15px;
    margin: 20px auto;
    padding-top: 55px;
    color: #fff;
}
</style>