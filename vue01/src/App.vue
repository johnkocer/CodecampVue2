<template>
  <div id="app">
    <h3>Vue Fundamentals</h3>
    <router></router>
    <hr>Provided by -SmartIT, John Kocer
  </div>
</template>

<script>
import router from "./routing.component";
export default {
  name: 'app',
  components: {
    router
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
