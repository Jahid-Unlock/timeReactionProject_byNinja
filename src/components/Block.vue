<template>
 <div class="block" v-if="showBlock" @click="stopTimer">
      <h5>click me</h5>
 </div>
</template>

<script>
export default {
    props : ['delay'],
    data(){
        return{
            showBlock : false,
            timer : null,
            reactionTime : 0
        }
    },

    mounted() {
       setTimeout(() =>{
           this.showBlock = true
           this.startTimer()
       },this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)

            this.$emit('end', this.reactionTime)


        }
    },
}
</script>

<style>
 .block{
     width: 400px;
     padding: 50px 0;
     text-align: center;
     border: 4px dashed #000;
     background: rgb(34, 63, 105);
     color: #fff;
     margin: 0 auto;
     margin-top: 30px;
 }
</style>