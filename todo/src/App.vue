<template>
  <div id="app">
    <h3>{{name}}'s Todo List</h3>
    <Todo></Todo>
    <hr>Provided by -SmartIT, John Kocer
  </div>
</template>

<script>
import Todo from "./components/todo.vue";
export default {
  name: "app",
  components: {Todo},
   data(){
    return{
      name:"John",
    }
  }
};
</script>

<style src="./assets/app.css" />
