<template>
  <div>
    <h4>Parent Component</h4>
    <p>{{color}}</p>
    <ChildComponent :handleClick="changeColor"/>
  </div>
</template>

<script>
import ChildComponent from './childComponent'
export default {
  name: "ParentComponent",
  components: {
    ChildComponent
  },

  props: {
    method: { type: Function }
  },
  data() {
    return {
      color: "Select a color"
    };
  },
  methods: {
    changeColor(event) {
      console.log(event.target.value);
      this.color = event.target.value;
    }
  }
};
</script>