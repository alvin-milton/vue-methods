<template>
  <div id="app">
    <h1>Methods</h1>
    <p>reusable bits of code</p>
    <p>Current status: {{ statusFromID(status) }}</p>
    <p>Filtering positive numbers</p>
    <ul>
      <li v-bind:key="number" v-for="number in filterPositive(numbers)"> {{ number }}</li>
    </ul>
    <p>Using this</p>
    <p>The sum of the positive numbers is: {{ getPositiveNumbersSum() }}</p>
    <p>Commputed propeties</p>
    <ul>
      <li>Cached by default</li>
      <li>Can also set values by using object setters</li>
    </ul>
    <p>The sum of numbers: {{ numberTotal }}</p>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      status: 2,
      numbers: [-5,6,-3,9,2,0,0.475, 0.999, 5]
    }
  },
  methods: {
    statusFromID(id) {
      const status = ({
        0: 'asleep',
        1: 'eating',
        2: 'learning vue'
      })[id]

      return status || 'unknown status: ' + id
    },
    filterPositive(numbers) {
      return numbers.filter((number) => number >= 0);
    },
    getPositiveNumbers(){
      return this.numbers.filter((number) => number >= 0)
    },
    getPositiveNumbersSum() {
      return this.getPositiveNumbers().reduce((sum, val) => sum + val)
    }
  },
  computed: {
    numberTotal() {
      return this.numbers.reduce((sum, val) => sum + val)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
