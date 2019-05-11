<template>
  <div>
    Helpers Works!
    <div v-if="show">HI JOHN</div>
    <br>
    <div :style="{display: show ? 'block' : 'none'} ">I ma a DIV</div>
    <button @click="toggle">Togle</button>
    <hr>
  </div>
</template>

<script>
import image from "@/images/BlueRose.jpg";
export default {
  name: "HelperComponent",
  
  methods: {
    toggle() {
      this.show = !this.show;
      console.log(this.show);
    }
  },

  data() {
    return {
      show: true
    };
  }
}; // end
</script>