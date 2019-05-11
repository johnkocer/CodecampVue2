<template>
  <div class="hello">
    EventBus
    <h1>{{ msg }}</h1>
    <Sibling1 name="Child" @childInput="input" ref="sibling1Ref"></Sibling1>
    <Sibling2 name="Child" @childInput="input" :sibling1Ref="$refs"></Sibling2>
  </div>
</template>

<script>
import Sibling1 from "./sibling1.vue";
import Sibling2 from "./sibling2.vue";
export default {
  inheritAttrs: true,
  name: "EventBus",
  components: {
    Sibling1,
    Sibling2
  },
  data: function() {
    return {
      msg: "EventBus"
    };
  },
  props: {
    value: String
  },
  mounted() {
    this.$root.$on("fromSibling1", arg1 => {
      console.log("fromSibling1", arg1);
      this.msg = arg1;
    });
  },
  methods: {
    input(arg1) {
      console.log("arg1: ", arg1);
      this.name = arg1;
    }
  }
};
</script>
