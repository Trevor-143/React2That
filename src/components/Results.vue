<template>
  <h4>This is your score  {{ got }} ms.</h4>
  <h4>{{ rank }}</h4>
</template>

<script>
export default {
    props: ['got'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.got < 300) {
            this.rank = 'Dont Leave Me Behind'
        }
        else if(this.got < 400) {
            this.rank = 'Nice, Better than Most'
        }
        else {
            this.rank = "You'll survive"
        }
    },
    updated() {
        console.log('Now showing Results');
    },
    unmounted() {
        console.log('Play again.');
    }
}
</script>

<style>

</style>