<template>
  <div >
   <h4>Child Component</h4>

      <button value="Red" @click='handleClick'>
        Red
      </button>

      <button value="Blue" @click='handleClick'>
        Blue
      </button>

      <button value="White" @click="handleClick">
        White
      </button>
  </div>
</template>

<script>

export default {
  name: 'ChildComponent',
   props: {
    handleClick: { type: Function },
  },
//    methods: {
//     changeColor(event) {
//       console.log(event.target.value);
//     }
//   },
 
 
}
</script>