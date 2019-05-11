<template>
  <div class="hello">
    <h1>{{ name }}</h1>
    <Child name="Child" @childInput="input"></Child>
  </div>
</template>

<script>
import Child from "./child.vue";
export default {
  name: "Parent",
  components: {
    Child
  },
  data: function() {
    return {
      name: "Parent"
    };
  },
  props: {
    value: String
  },
  methods: {
    input(arg1) {
      console.log("arg1: ", arg1);
      this.name = arg1;
    }
  }
};
</script>
