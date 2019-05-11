<template>
  <div id="app">
    <router></router>
    <hr>Copyright 2019 (c) SmartIT. All rights reserved.
    <br>SmartIT - John Kocer
  </div>
</template>

<script>
import router from "./routing.component";

export default {
  name: "app",
  components: {
    router
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
</style>
