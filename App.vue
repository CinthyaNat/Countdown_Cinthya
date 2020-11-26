<template>
  <div id="app">
    <HelloWorld 
    :time-left="timeLeft"
    />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      timeLimit: 20,
      timerInterval: null,
      timePassed: 0
    }
  },
  mounted() {
    this.startTimer();
  },
  methods: {
    startTimer() {
      this.timerInterval = setInterval(() => (this.timePassed += 1), 1000);
    }
  },
  
  computed: {
    timeLeft() {
      return this.timeLimit - this.timePassed
    },
    formattedTimeLeft() {
      const timeLeft = this.timeLeft
      // The largest round integer less than or equal to the result of time divided being by 60.
      const minutes = Math.floor(timeLeft / 60)
      // Seconds are the remainder of the time dividedby 60 (modulus operator)
      let seconds = timeLeft % 60
      // If the value of seconds is less than 10,then display seconds with a leading zero
      if (seconds < 10) {
        seconds = `0${seconds}`
      }
      // The output in MM:SS format
      return `${minutes}:${seconds}`
    
  }}

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
