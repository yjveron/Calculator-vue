<template>
<!-- OR WHAT IF CALCULATOR IS THE PARENT COMPONENT OF RECENT EQUATIONS, IMBIS NA APP IS PARENT OF RECENT
EQUATIONS. KASO.. SMART BA YUN? -->

  <div id="app">
    <Calculator v-bind:equation="equation" @compute="saveEquation($event)" />
    <ol class="hi">
      <h3>Recent Equations</h3>
      <li v-for="(item, index) in recentEquations" v-bind:key="index">{{item}}</li>
    </ol>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue';

export default {
  name: 'app',
  components: {
    Calculator
  },
  data() {
    return{
      equation: '',
      recentEquations: []
    }
  },
  methods: {
    saveEquation(pulledEquation){
      this.equation = pulledEquation
      this.recentEquations.push(
        this.equation)
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  display: flex;
  justify-content: center;
  margin-top: 60px;
  width: 100vw;
  text-align: center;
  background-color: darkgrey;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50; */
}

.hi{
  margin-left: 30px;
}
</style>
