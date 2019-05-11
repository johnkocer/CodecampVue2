<template>
  <div id="app">
    <!-- <MyInheritance></MyInheritance> -->
    <!-- <MyList></MyList> -->
    <ArrayOfObject></ArrayOfObject>
  </div>
</template>

<script>
import MyInheritance from "./myInheritence.vue";
import MyList from "./myList"
import ArrayOfObject from "./arrayOfObject"

export default {
  name: 'app',
  components: {
    MyInheritance,
    MyList,
    ArrayOfObject
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
