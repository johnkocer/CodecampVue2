<template>
  <div class="hello">
    <hr>Sibling2
    <h1>{{ msg }}</h1>
    Direct Acsess: {{inputTextRefValue}}
  </div>
</template>

<script>
export default {
  name: "Sibling2",
  data: function() {
    return {
      msg: "Sibling2",
      inputTextRefValue: "REF"
    };
  },
  props: {
    name: String,
    value: String,
    sibling1Ref: {}
  },
  mounted() {
    this.$root.$on("fromSibling1", arg1 => {
      console.log("fromSibling1", arg1);
      this.msg = arg1;
      let ret = this.sibling1Ref;
      this.inputTextRefValue = ret.sibling1Ref.inputText;
      console.log("in", ret.sibling1Ref.inputText);
    });
  }
};
</script>
