<template>
  <div class="result">

    <h1>Reaction time : {{ score }} ms</h1>
    <p>{{ rank }}</p>
  </div>
</template>

<script>
export default {
props: [
    'score'
],

data() {
    return {
     rank:null
    }
},

mounted() {
    if(this.score < 250) {
        this.rank = 'pretty fast'
    }

    else if (this.score < 500) {
       this.rank = 'quite fast'
    }

    else {
        this.rank = 'slowwwwwww'
    }
}

}
</script>

<style>
.result h1 {
    color: rgb(75, 191, 73);
}
</style>