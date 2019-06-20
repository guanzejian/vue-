<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <Coustmer/>
  </div>
</template>

<script>
import Coustmer from './components/coustmer'

export default {
  name: 'App',
  components: {
    Coustmer
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
