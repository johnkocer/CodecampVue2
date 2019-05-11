<template>
  <div>
    <div>Text Value: {{textValue}}</div>
    <input type="text" defaultValue="JOHN" v-model="textValue" ref="textRef" @change="onChange">

    <input type="button" value="Focus the text input" @click="focusTextInput">
  </div>
</template>

<script>
export default {
  name: "Ref",

  data() {
    return {
      textValue: ""
    };
  },
  methods: {
    focusTextInput() {
      this.$refs.textRef.focus();
    },
    onChange(e) {
      console.log(e.target.value);
      console.log("Ref value:", this.$refs.textRef.value);
    }
  }
};
</script>
