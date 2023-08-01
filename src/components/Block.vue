<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
      <h2 >click me</h2>
    </div>
</template>

<script>
export default {
    data() {
    return  {
        showBlock: false,
        timer: null,
        reactionTime: 0
    }
    },

    props: [
        'delay',
    ],

    mounted() {
        console.log('mounted')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
        }, this.delay);
    },

    methods: {
     startTimer() {
       this.timer = setInterval(() => {
         this.reactionTime += 10
       }, 10);
     },

     stopTimer() {
       clearInterval(this.timer)
       this.$emit("end", this.reactionTime)
     }

    },



    updated() {
    console.log('updated')
    }
}

</script>


<style>
.block {
  width: 400px;
  margin: 30px auto;
  padding: 100px;
  background-color: #36dbf4; /* Red */
  color: white;
  border-radius: 15px;
}

</style>