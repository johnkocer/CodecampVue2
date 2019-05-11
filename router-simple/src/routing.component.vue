<template>
  <div>
    <nav>
      <router-link to="/" exact>Home</router-link>|
      <router-link to="/contact">Contact</router-link>|
      <router-link to="/about">About</router-link>
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>
/* eslint-disable */
import Vue from "vue";
import VueRouter from "vue-router";
import Home from "./home";
import Contact from "./contact";
import About from "./about";
Vue.use(VueRouter);

export default new VueRouter({
  routes: [
    { path: "/", component: Home },
    { path: "/contact", component: Contact },
    { path: "/about", component: About }
  ]
});
</script>

<style>
</style>
