<template>
  <div id="app">
    <Calculator />
    <p>Designed and Coded by <a class='link' href='https://www.freecodecamp.org/matthewhtc' target='_blank'>Matthew Chan</a>.</p>
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
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

a.link, a.link:visited {
  text-decoration: none; 
}
a.link:visited {
  color: #2c3e50;
}

a.link:hover {
  color: darken(#FF5722, 10%);
  transition: .25s ease;
}

body, html {
  margin: 0;
  height: 100%;
  background-color: lightgrey;
}
</style>
