<template>
  <div>Template Works!</div>
</template>
      <script>
export default {
  name: "Template",
  // put child components here
  components: {},
  // variables passed from parent template
  props: {},
  // scoped variables in this component
  data() {
    return {
      name: "John"
    };
  },
  // observed variables (by function)
  computed: {
    reversedName() {
      return this.name
        .split("")
        .reverse()
        .join("");
    }
  },
  // functions firing by template
  methods: {
    changeMessage() {
      this.name = "Good bye Mike";
    }
  },
 
  // Lifecycle hooks
  created() {},
  mounted() {},
  updated() {},
  destroyed() {}
};
</script>
<style>
</style>
