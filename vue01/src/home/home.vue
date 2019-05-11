<template>
  <div>
    Property Binding - Import the Image then use it
    <br>
    <img :src="image">
    <img src="@/assets/BlueRose.jpg">
    <br>Property Binding - use require
    <br>
    <img :src="require('@/assets/BlueRose.jpg')">
    <div class="logo">
      <img src="@/assets/logo.png" width="100" height="50">
    </div>
    <br>
    <button @click="togle()" :disabled="isDisabled">Click Me</button>
    <button @click="togle()" :disabled="!isDisabled">Click Me</button>
  </div>
</template>

<script>
//import image from "@/assets/logo.png"
import image from "@/images/BlueRose.jpg";
export default {
  name: "Home",
  methods: {
    togle() {
      this.isDisabled = !this.isDisabled;
      console.log(this.isDisabled);
    },
    getFullName: function() {
      return "j KOCER";
    }
  },

  data() {
    return {
      isDisabled: false,
      rose: "@/assets/BlueRose.jpg",
      image: image
    };
  }
}; // end
</script>