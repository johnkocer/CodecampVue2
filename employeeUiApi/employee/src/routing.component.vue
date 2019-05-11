<template>
  <div>
    <nav>
      <router-link to="/" exact>Home</router-link>|
      <router-link to="/counter">Counter</router-link>|
      <router-link to="/fetchData">Fetch Data</router-link>|
      <router-link to="/employee">Employee</router-link>
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>
/* eslint-disable */
import Vue from "vue";
import VueRouter from "vue-router";
import Home from "@/home/home";
import Counter from "@/counter/counter";
import FetchData from "@/fetch-data/fetch-data";
import Employee from "./employee/employee";
Vue.use(VueRouter);

export default new VueRouter({
  mode: 'history',
  routes: [
    { path: "/", component: Home },
    { path: "/counter", component: Counter },
    { path: "/fetchData", component: FetchData },
    { path: "/employee", component: Employee }
  ]
});
</script>

<style>
</style>
