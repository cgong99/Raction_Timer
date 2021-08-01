<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {//before this component added into DOM
        console.log('component mounted')
        setTimeout(() => {  // setTimeout runs the first part after the time in the second paramater
            this.showBlock = true
            this.startTimer()   
        }, this.delay)
        
    },
    updated() {//runs when block updated
        console.log("updated")
    },
    unmounted() { //runs when this component has been unmounted(not in the Dom)
        console.log('unmounted')
    },

    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>