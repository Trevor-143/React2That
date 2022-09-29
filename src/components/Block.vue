<template>
  <div class="block" v-if="showBlock" @click ="stopTimer">
    Click Fast
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reacting: 0
        }
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reacting += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reacting)
            this.$emit('finished', this.reacting)
        }
    },
    mounted() {
        console.log("mounted");
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
        }, this.delay)
    },
    updated() {
        console.log('Now showing Cicle');
    },
    unmounted() {
        console.log('Cicle Gone, Check Your score.');
    }
}
</script>

<style>
    body {
        display: flex;
        justify-content: center;
        align-items: center;
        height: inherit;
    }
.block {
    width: 400px;
    height: 400px;
    color: #ffffff;
    font-size: 38px;
    border-radius: 50%;
    background: #864d4d;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>