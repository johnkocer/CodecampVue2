<template>
  <fieldset>
    <legend>
      <span style="font-weight: bold">Payment Info:</span>
    </legend>
    <div ng-style="isMemberSuccess">
      <div>
        <div>
          <label class="paymentTH">Payment Type:</label>
          <select @change="OnPaymentTypeChange($event)" ref="paymentSourceRef">
            <option
              v-bind:key="paymentType.id"
              v-bind:value="JSON.stringify(paymentType)"
              v-for="paymentType in this.paymentTypeList"
            >{{paymentType.text}}</option>
          </select>
        </div>
        <div>
          <label class="paymentTH">Credit Card Number</label>
          <br>
          <input
            type="text"
            v-bind:model="payment.creditCardNumber"
            placeholder1="Enter Credit Card Number"
            numbers-only
            required
            class="number-input"
            size="16"
            maxsize="16"
            value="4111111111111111"
          >
        </div>
        <div class style="float: left; margin-left: 60px; width: 180px;">
          <label class="paymentTH">Expiry Date</label>
          <br>
          <input
            type="text"
            id="expiryDate"
            name="expiryDate"
            v-bind:model="payment.expirationDate"
            numbers-only
            required
            class="number-input"
            size="10"
            maxsize="10"
            value="01/12/2020"
          >
        </div>
        <div class="ml-5" style="float: left; margin-left: 10px; width: 100px;">
          <label class="paymentTH">Security code</label>
          <br>
          <input
            type="text"
            id="creditCardNumber"
            name="creditCardNumber"
            v-bind:model="payment.cvv"
            placeholder="Enter Credit Card Number"
            numbers-only
            required
            class="number-input"
            size="4"
            maxsize="4"
            value="911"
          >
        </div>
      </div>
      <br>
      <br>
      <div class="ml-1">
        <br>
        <label class="paymentTH">Payment Amount:</label>
        <br>$
        <input
          type="text"
          id="paymentAmount"
          name="paymentAmount"
          size="5"
          ref="paymentAmountRef"
          :value="selectedProduct.price"
          placeholder="100"
        >
        <br>
        <br>
        <button
          class="btn btn-success btn-sm"
          @click="handleMakePaymentClick()"
          type="submit"
        >Process Payment</button>
      </div>
      <br>
      <label>{{paymentMessage}}</label>
    </div>
  </fieldset>
</template>

<script>
/* eslint-disable */

import { PaymentService } from "../service/payment.service";
import { Member, Payment, Product } from "../service/app.classLibrary";

const paymentTypeList = [
  { text: "Visa", value: "Visa" },
  { text: "Mastercard", value: "Mastercard" },
  { text: "Discover", value: "Discover" },
  { text: "AmericanExpress", value: "AmericanExpress" },
  { text: "SearsCard", value: "SearsCard" },
  { text: "SearsGiftCard", value: "SearsGiftCard" }
];

export default {
  name: "PaymentComponent",
  props: {
    paymentAmountRef: {}
  },
  data() {
    return {
      payment: Payment,
      member: Member,
      paymentTypeList: paymentTypeList,
      paymentMessage: String,
      selectedProduct: Product,
      showEditor: true,
      myName: "",
      newEmployee: { id: 0, name: "", gender: "", salary: 0, departmentId: 1 },
      findEmployee: { id: 0, name: "", gender: "", salary: 0, departmentId: 1 }
    };
  },
  mounted() {
    this.paymentMessage = "";
    this.payment = new Payment();
    console.log("in Mounted");

    this.$root.$on("emitFromMember", member => {
      console.log("emitFromMember", member);
      this.member = member;
      console.log("in on-emitFromMember", member);
    });

    this.$root.$on("emitFromSelectedProduct", selectedProduct => {
      this.selectedProduct = selectedProduct;
      console.log("in on-emitFromSelectedProduct", selectedProduct);
    });
  },

  methods: {
    OnPaymentTypeChange(event) {
      // We left this event as an example, but it is doing nothing except clearing the credit cart number
      // We are getting payment source via ref
      let value = JSON.parse(event.target.value);

      console.log("In OnPaymentTypeChange: ", value);
      this.payment.creditCardNumber = "";
    },

    handleMakePaymentClick() {
      this.payment.nameOnCard = this.member.fullName;
      this.payment.member = this.member;
      this.payment.paymentAmount = this.$refs.paymentAmountRef.value;
      this.payment.paymentSource = JSON.parse(
        this.$refs.paymentSourceRef.value
      ).value;
      console.dir(this.payment);
      // validate inputs here
      if (this.payment.paymentAmount == "") {
        this.paymentMessage = "Select Payment!";
        return;
      }
     this.makePayment(this.payment);
    },

    makePayment(payment) {
      if (!payment) {
        return;
      }

      PaymentService.makePayment(payment)
        .then(data => {
          this.paymentMessage = data.paymentMessage;
          console.log("Payment processed: " + this.paymentMessage);
        })
        .catch(error => {
          console.log("Error in make payment" + error);
        });
    }
  } // methods
};
</script>

