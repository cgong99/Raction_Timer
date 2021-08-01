<template>
<div>
    <p>Reaction Time: {{score}} ms</p>
    <p class="level">{{level}}</p>
</div>
</template>

<script>
export default {
    props: ["score"],
    data() {
        return {
            level: null
        }
    },

    mounted() {
        if (this.score < 210) {
            this.level = "God level!"
        }else if (this.score < 250) {
            this.level = "Very Fast!"
        } else if (this.score < 300) {
            this.level = "Rapid reaction!"
        } else if (this.score < 400) {
            this.level = "Average"
        } else {
            this.level = "Snail pace..."
        }
    }
}
</script>

<style>
    .level{
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>