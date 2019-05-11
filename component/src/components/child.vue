<template>
  <div class="hello">
    <h1>{{ name }}</h1>
    <input type="text" :value="value" @input="triggerEvent">
  </div>
</template>

<script>
export default {
  name: "Child",
  props: {
    name: String,
    value: String
  },
  methods: {
    triggerEvent(event) {
      console.log("In triggreEvent");
      this.$emit("childInput", event.target.value);
    }
  }
};
</script>
