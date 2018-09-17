<template>
  <div id="app">
    <Calculator />
  </div>
</template>

<script>
import Calculator from '@/components/Calculator';

export default {
  name: 'app',
  components: {
    Calculator
  }
}
</script>
<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body, html {
  margin: 0;
  height: 100%;
  background-color: lightgrey;
}
</style>
