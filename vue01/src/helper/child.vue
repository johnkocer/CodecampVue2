<template>
  <div>
    <h2 class="bg-primary text-white text-center p-2">
      <div>Props Value: {{value}}</div>
      <div>Local Value: {{counter}}</div>
    </h2>
    <div class="text-center">
      <button class="btn btn-primary m-2" @click="callback">Parent</button>

      <button class="btn btn-primary m-2" @click="incrementCounter">Local</button>
      <br>
      CityList: {{JSON.stringify(this.cityList)}}
      <br>
      <button class="btn btn-primary m-2" @click="callbackObj(cityList)">Parent Object</button>
    </div>

    <div>Props Value: {{JSON.stringify(selectedAnimal)}}</div>

    <ul class="todos">
      <li v-for="(item, index) in animals" :key="index" @click="callbackAnimalObj(item)">
        <span class="badge">{{item.id}}</span>
        - {{item.name}}
      </li>
    </ul>
    <hr>
    <select @change="callbackOnChangeAnimal">
      <option
        v-for=" (item, index) in animals"
        :key="item.name+index"
        :value="JSON.stringify(item)"
      >{{item.name}}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Child",

  props: {
    value: { type: String },
    cityList: { type: Array },
    animals: { type: Array },
    callback: { type: Function },
    callbackSelectedAnimal: { type: String },
    callbackObj: { type: Function },
    callbackAnimalObj: { type: Function },
    callbackOnChangeAnimal: { type: Function }
  },
  data() {
    return {
      counter: 1,
      selectedAnimal: ""
    };
  },
  methods: {
    incrementCounter() {
      this.counter = this.counter + 1;
    }
  }
};
</script>
