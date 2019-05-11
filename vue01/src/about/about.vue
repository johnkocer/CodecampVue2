<template>
  <div>
    About Works!
    <!-- <HelperComponent></HelperComponent> -->
    <!-- <CalbackComponent value={ this.state.city } callback={ this.changeCity }></CalbackComponent> -->
    <!-- <CalbackComponent ></CalbackComponent> -->
    <Ref></Ref>

  </div>
</template>

<script>
import HelperComponent from "../helper/helper.component";
import CalbackComponent from "../helper/callback";
import Ref from "../helper/ref";

export default {
  name: "About",
  components: {
    HelperComponent,
    CalbackComponent,
    Ref
  }
};
</script>