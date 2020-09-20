<template>
  <div id="app">
    <countdown></countdown>
  </div>
</template>

<script>
  import countdown from "./countdown.vue"
  export default {
    data() {
      return {
        message: 'Hola en vue',
      };
    },
    components:{countdown},
  }
</script>

<style scoped>
 #app {
    text-align: center;
    font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: gray;
    border: 1px solid cadetblue;
    padding: 20px;
   

  }

  
 

</style>