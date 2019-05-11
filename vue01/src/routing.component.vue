<template>
  <div>
    <nav>
      <router-link to="/" exact>Home</router-link>|
      <router-link to="/contact">Contact</router-link>|
      <router-link to="/about">About</router-link> | 
      <router-link to="/twoway">Two Way Databinding</router-link>
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>
/* eslint-disable */
import Vue from "vue";
import VueRouter from "vue-router";
import Home from "@/home/home";
import Contact from "@/contact/contact";
import About from "@/about/about";
import DataBindingTwoWay from "./twoway/dataBindingTwoWay"
Vue.use(VueRouter);

export default new VueRouter({
  routes: [
    { path: "/", component: Home },
    { path: "/contact", component: Contact },
    { path: "/twoway", component: DataBindingTwoWay },
    { path: "/about", component: About }
  ]
});
</script>

<style>
</style>
