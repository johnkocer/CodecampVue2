<template>
  <div>
    <h4>Parent Component</h4>
    <Child
      :value="city"
      :cityList="cityList"
      :animals="animals"
      :callback="changeCity"
      :callbackObj="changeCityObj"
      :callbackAnimalObj="changeAnimalObj"
      :callbackOnChangeAnimal="onChangeAnimal"
    />
  </div>
</template>

<script>
/* eslint-disable */
const cities = [{ id: 1, name: "Istanbul" }, { id: 2, name: "New York" }];
const animals = [
  { id: 1, name: "CAT" },
  { id: 2, name: "DOG" },
  { id: 3, name: "FROG" }
];

import Child from "./child";
export default {
  name: "CallbackComponent",
  components: {
    Child
  },

  props: {
    method: { type: Function }
  },
  data() {
    return {
      textValue: "JOHN",
      city: "Istanbul",
      cityList: cities,
      selectedAnimal: String,
      animals: animals
    };
  },
  methods: {
    changeCity() {
      this.city = this.city === "Istanbul" ? "New York" : "Istanbul";
    },

    changeCityObj(obj) {
      console.log(JSON.stringify(obj));
      this.cityList = obj;
    },

    callbackSelectedAnimal(obj) {
      console.log(JSON.stringify(obj));
      this.selectedAnimal = JSON.stringify(obj);
    },
    changeAnimalObj(obj) {
      console.log(JSON.stringify(obj));
      this.selectedAnimal = obj;
    },

    onChangeAnimal(event) {
      console.log(JSON.parse(event.target.value));
    }
  }
};
</script>
