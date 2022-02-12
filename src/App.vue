<template>
  <div id="app">
    <div class="main">
      <!-- <svg width="200" height="200" viewBox="0 0 100 100"> -->
      <svg>
        <circle class="circle"/>
        <circle class="progress" :style="{'stroke-dashoffset': offset}"/>
      </svg>
      <div class="number">{{percent}} %</div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data(){
    return{
      offset: -251,
      percent: 0
    }
  },
  created(){
    var intval = setInterval(() => {
      //console.log(">>>" + this.offset);
      if(this.offset > -500){
        this.offset -= 1;
        this.percent = ((251 / 100) * this.percent) + 1;
      }
      else{
        //this.offset = -251;
        clearInterval(intval);
        intval
      }
    }, 100);
  }//,
  // computed:{
  //   percentage(){
  //     return this.percent.toFixed();
  //   }
  // }
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
svg {
  border: 1px solid #aaa; 
  position: relative;
  width: 100px;
  height: 100px;
}
.circle{
  /* width: 100px;
  height: 100px; */
   /* cx="50" cy="50" r="40" stroke="blue" stroke-width="5" fill="lightgrey" */
  cx: 50px;
  cy: 50px;
  r: 40px;
  /* stroke: lightgrey;
  stroke-width: 0.1px; */
  fill: none;
}
.progress{
  /* width: 100px;
  height: 100px; */
   /* cx="50" cy="50" r="40" stroke="blue" stroke-width="5" fill="lightgrey" */
  cx: 50px;
  cy: 50px;
  r: 40px;
  stroke: blueviolet;
  stroke-width: 5px;
  fill: none;
  /* stroke-dasharray: 1 250;
  stroke-dashoffset: -1; */
  stroke-dasharray: 251 251; /* cs=50 x cy=50 = 250 */
  stroke-dashoffset: -251;   /* -251 */
  stroke-linecap: round;
}
.main .number{
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
}
</style>
