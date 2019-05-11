<template>
  <div>
    <h1>Counter</h1>
    <p>This is a simple example of an Vue component.</p>
    <p>
      Current count:
      <strong>{{ currentCount }}</strong>
    </p>
    <button class="btn-sm btn-success" @click="incrementCounter()">Increment</button>
  </div>
</template>

<script>
export default {
  name: "Counter",

  data() {
    return {
      currentCount: 0
    };
  },

  methods: {
    incrementCounter() {
      this.currentCount++;
    }
  }
};
</script>