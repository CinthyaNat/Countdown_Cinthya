<template>
  <div id="app">
    <div class="center"><h1><i class="fa fa-hourglass-start"></i>  SIMPLE COUNTDOWN  <i class="fa fa-hourglass-end"></i></h1></div>
    <br><br>
    <div class="center" id="example-1">
      <h2 v-if="visible">{{timeremaining}}</h2></div> 
    <div class="center" id="example-1">
      <button class="btn" v-on:click="counterhour += 1" v-if="!isHidden"><i class="fa fa-arrow-up"></i></button>
      <button class="btn" v-on:click="counterminute += 1" v-if="!isHidden"><i class="fa fa-arrow-up"></i></button>
      <button class="btn" v-on:click="countersecond += 1" v-if="!isHidden"><i class="fa fa-arrow-up"></i></button>
    </div>
    <div class="center time" id="example-1">
      <h4>{{ counterhour }}   :  {{ counterminute }}  :  {{ countersecond }} </h4>
    </div>
    <div class="center">
      <button class="btn" v-on:click=kurangcounterH() v-if="!isHidden"><i class="fa fa-arrow-down"></i></button>
      <button class="btn" v-on:click=kurangcounterM() v-if="!isHidden"><i class="fa fa-arrow-down"></i></button>
      <button class="btn" v-on:click=kurangcounterS() v-if="!isHidden"><i class="fa fa-arrow-down"></i></button>
    </div> <br>
    <div class="center">
      <button class='start manual' v-on:click=countDownTimer() v-if="!isHidden">Start</button>
    </div>
    <div class="center pad">
      <button class='start manual' v-on:click=pause() v-if="visible1">Pause</button>
      <button class='start manual' v-on:click=resume() v-if="paused">Resume</button>
      <button class='start manual2' v-on:click=reset() v-if="visible">Reset</button>
    </div>
        <HelloWorld 
    :time-left="timeLeft"
    />

  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: 'App',
  el : '#example-1',
  components: {
    HelloWorld
  },
  data() {
    return {
      counterminute : 0,
      counterhour : 0,
      countersecond : 0,
      deleteClicked : false,
      isHidden: false,
      visible : false,
      count: null,
      paused : false,
      visible1 : false,
      

    }
  },
  methods: {
    kurangcounterS(){
      if(this.countersecond > 0) {
        this.countersecond -= 1
        }
  
    },
    kurangcounterM(){
      if(this.counterminute > 0) {
        this.counterminute -= 1
      }
    },
    kurangcounterH(){
      if(this.counterhour > 0) {
        this.counterhour -= 1
      }
    },
    resume(){
      this.paused = false
      this.visible1 = true
      setTimeout(this.countDownTimer(), 1000);

    },
    pause(){ 
      this.paused = true   
      this.visible1 = false 
      setTimeout(this.countDownTimer(), 10000000);
    },
    reset(){
       window.location.reload()
    },
    countDownTimer() {
                this.isHidden = true
                this.visible=true
                this.visible1 = true
                this.timeremaining = "Time Remaining"
                if(this.countersecond>0) {
                    setTimeout(() => {           
                      this.countersecond -= 1
                        this.countDownTimer()
                    }, 1000)
                } 
                else if (this.countersecond==0 & this.counterminute>0){
                  setTimeout(() =>{this.counterminute -=1
                  this.countersecond+=59
                  this.countDownTimer()
                },1000)
                }
                else if (this.countersecond==0 & this.counterminute==0 & this.counterhour>0){
                  setTimeout(() =>{this.counterhour -=1
                  this.counterminute+=59
                  this.countersecond+=59
                  this.countDownTimer()
                },1000)
                }
                else if (this.countersecond==0 & this.counterminute==0 & this.counterhour==0){
                  this.timeremaining="BOOOM!!!!!",
                  this.deleteClicked = true;
                  document.body.className = "red";
                }
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
#example-1{
  word-spacing: 10px;
}
.btn{
  padding: 20px;
}
body {
  background-color:#46d4bc;
}
.red {
  background-color:#60e354;
}
.mint {
  background-color:#46d4bc;
}
.time{
  padding: 20px;
}
.manual{
  background-color: #ced2d9;
  width : 120px;
  padding: 10px;
  border: none;
}
.manual2{
  background-color: #ff5b4f;
  width : 120px;
  padding: 10px;
  margin: 20px;
  border: none;
}

.pad{
  padding: 20px;
}


</style>
