<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Parent name='Parent'></Parent>
    <!-- <EventBus></EventBus> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import Parent from './components/parent';
import EventBus from './components/eventBus'

export default {
  name: 'app',
  components: {
    // HelloWorld,
    Parent,
    EventBus
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
