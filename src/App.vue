<template>
  <h1>React to the timer</h1>
  <button @click="now" :disabled="isOn">Play</button>
  <Block v-if="isOn" :delay="delay" @finished = "theEnd"/>
  <Results v-if="showGot" :got="got" />
  <!-- <p v-if="showGot">How fast Are you:  {{ got }} ms</p> -->
</template>

<script>
  import Block from './components/Block.vue'
  import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isOn: false,
      showGot: false,
      delay: null,
      got: null
    }
  },
  components: { Block, Results },
  methods: {
    now() {
      this.delay = 2000 + Math.random() * 5000
      this.isOn = true
      this.showGot = false
      console.log(this.delay);
    },
    theEnd(score) {
      this.got = score
      this.isOn = false
      this.showGot = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #6d0e0e;
  margin-top: 60px;
}
button {
  margin: 10px;
  background: rgb(131, 23, 23);
  border: none;
  padding: 10px 15px;
  color: #ffffff;
  width: fit-content;
  border-radius: 10px;
  cursor: pointer;
}
button[disabled] {
  cursor: not-allowed;
  opacity: 0.4;
}
</style>
