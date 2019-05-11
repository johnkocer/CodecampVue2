<template>
  <fieldset>
    <legend>
      <span style="font-weight: bold">Products:</span>
    </legend>
    <div style="display: table;">
      <div style="display: table-row">
        <div style="display: table-cell; min-width: 150px; " class="paymentTHBold">Products</div>
        <div
          style="display: table-cell; width: 110px; margin-left: 10px;"
          class="paymentTHBold"
        >&nbsp;&nbsp;&nbsp;Total Price</div>
        <div
          style="display: table-cell; width: 150px; margin-left: 10px;"
          class="paymentTHBold"
        >&nbsp;&nbsp;&nbsp;Monthly Payment</div>
      </div>
      <div style="display: table-row">
        <div style="display: table-cell;">
          <select @change="onProductListChange($event)">
            <option>Select</option>
            <option
              v-bind:value="JSON.stringify(product)"
              v-for="product in productList"
              v-bind:key="product.id"
            >{{product.name}}</option>
          </select>
        </div>
        <div style="display: table-cell;">
          $
          <input
            type="text"
            class="paymentTHBold"
            disabled="true"
            style="margin-left: 1px;width: 60px;"
            :value="selectedProduct.price"
          >
        </div>
        <div style="display: table-cell;">
          $
          <input
            type="text"
            class="paymentTHBold"
            disabled="true"
            style="margin-left: 1px;width: 60px;"
            :value="montlyPayment"
          >
        </div>
      </div>
    </div>
  </fieldset>
</template>

<script>
/* eslint-disable */
import { PaymentService } from "../service/payment.service";
import { Product } from "../service/app.classLibrary";

export default {
  name: "ProductComponent",
  props: {
    //msg: String
  },
  data() {
    return {
      productList: [],
      selectedProduct: Product,
      montlyPayment: 0
    };
  },
  mounted() {
    console.log("in Mounted");
    this.getProductList();
  },
  methods: {
    getProductList() {
      PaymentService.getProductList()
        .then(res => {
          console.dirxml(res.data);
          this.productList = res.data;
        })
        .catch(error => {
          console.log("There is an error in Get API call." + error);
        });
    },

    triggerSelectedProductEvent() {
      console.log("In triggreEvent", this.selectedProduct);
      this.$root.$emit("emitFromSelectedProduct", this.selectedProduct);
    },

    onProductListChange(event) {
      console.log("In onProductListChange: " + event.target.value);
      this.selectedProduct = JSON.parse(event.target.value);
      this.montlyPayment = this.selectedProduct.price / 12;
      this.triggerSelectedProductEvent();
    }
  } // methods
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

