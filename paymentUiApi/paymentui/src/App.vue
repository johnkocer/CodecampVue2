<template>
  <div >
    <h3>Payment Processing</h3>
    <Member></Member>
    <Product></Product>
    <Payment></Payment>
    <hr>
    Provided by -SmartIT, John Kocer
  </div>
</template>

<script>
import Member from "./member/member";
import Product from "./product/product";
import Payment from "./payment/payment";
export default {
  name: "app",
  components: {
    Member,
    Product,
    Payment
  }
};
</script>

<style src="./assets/app.css" />
