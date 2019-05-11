<template>
  <div class="hello">
    <hr>Sibling1
    <h1>{{ name }}</h1>
    <input type="text" :value="value" @input="triggerEvent">
  </div>
</template>

<script>
export default {
  name: "Sibling1",
  data: function() {
    return {
      inputText: String
    };
  },
  props: {
    name: String,
    value: String
  },
  methods: {
    triggerEvent(event) {
      console.log("In triggreEvent");
      this.inputText = event.target.value;
      this.$root.$emit("fromSibling1", event.target.value);
    }
  }
};
</script>
