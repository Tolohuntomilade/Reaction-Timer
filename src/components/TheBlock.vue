<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock:false,
            timer:null,
            reactionTime:0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock=true
            this.startTimer()
        }, this.delay);
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    },
    // updated() {
    //     console.log("Component Updated")
    // },
}
</script>

<style>
    .block{
        width: 200px;
        border-radius: 30px;
        background-color:rgb(7, 85, 27);
        color:white;
        text-align: center;
        padding: 20px 0px;
        margin: 40px auto;
        font-weight: bold;
        font-size: larger;
        cursor: pointer;
        letter-spacing: 2px;
    }
</style>