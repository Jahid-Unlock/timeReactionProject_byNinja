<template>
    <p>Result is : {{reactionTime}} ms</p>
    <h2>{{rank}}</h2>
</template>

<script>
export default {
   props : ['reactionTime'],
   data(){
       return{
           rank : null
       }
   },
   mounted() {
       if(this.reactionTime < 300){
           this.rank = "You are too first, COOL!"
       } else if (this.reactionTime < 700) {
           this.rank = "You are good."
       } else {
           this.rank = "you are slow! You have to act first."
       }
   },
}
</script>

<style>

</style>