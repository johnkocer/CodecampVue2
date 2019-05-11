<template>
  <div>
    <!-- <h3>Name is {{ ' ' + name}}</h3>
    <input type="text" v-model="name" placeholder="Enter a name">
    <hr>
    <h3>Selected Name is {{ ' ' + selectedName}}</h3>

    <select v-model="selectedName" @change="handleChange">
      <option disabled value>Choose a name</option>
      <option>Jack</option>
      <option>Amy</option>
      <option>Mary</option>
    </select> -->
    <hr>
    <ParentComponent></ParentComponent>
  </div>
</template>

<script>
import ParentComponent from './parentComponent'

export default {
  name: "DataBindingTwoWay",
  components: {
    ParentComponent
  },

  methods: {
    handleChange(event) {
      console.log(event.target.value);
    }
  },

  data() {
    return {
      name: "",
      selectedName: ""
    };
  }
}; // end
</script>