<template>
  <div id="app">

    <h1 id="title">{{message}}</h1>
    <span id="counter">{{countdown}}</span>

    
    <div id="timers">
    <button @click="count(3)">3s</button>
     <button @click="count(60)">1m</button>
     <button @click="count(300)">5m</button>
     <button @click="count(600)">10m</button>
     <button @click="count(1800)">30m</button>
     </div>
  </div>
 
 
</template>

<script>
let intervalTime;
  export default {
      name: "countdown",
    data() {
      return {
        message: 'Cuenta Regresiva',
        countdown:"00:00"
        
      };
    },
    methods:{
        count:function(seconds){
            clearInterval(intervalTime)
                const now = Date.now();
                const end = now + ((seconds+1) *1000);
                this.stopInterval(end)
        },
        stopInterval:function(end){
            intervalTime= setInterval(()=>{
            const resto = Math.round((end-Date.now())/1000);
            if (resto<0){
                clearInterval(intervalTime);
                return
            }
            const minutes = Math.floor((resto %3600)/60);
            const seconds = resto % 60;
            if((String(seconds).length)===1 && (String(minutes).length)===1){
                this.countdown=`0${minutes}:0${seconds}`
            } else if((String(seconds).length)===1 && (String(minutes).length)!=1){
                this.countdown=`${minutes}:0${seconds}`
            } else if((String(seconds).length)!=1 && (String(minutes).length)===1){
                this.countdown=`0${minutes}:${seconds}`
            } else{
                this.countdown=`${minutes}:${seconds}`
            }
        },1000)
    }
  },

  }
</script>

<style scoped>
  #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
 

  }
  #timers{
      margin-top: 30px;
  }
    button{
      padding: 5px 20px;
      color: black;
      background: white;
      border: none;
      margin-left: 20px;
      -webkit-box-shadow: 3px 4px 5px 0px rgba(184,173,184,1);
      -moz-box-shadow: 3px 4px 5px 0px rgba(184,173,184,1);
      box-shadow: 3px 4px 5px 0px rgba(184,173,184,1);
  }
  button:hover{
      background:black;
      color: white;
  }
</style>