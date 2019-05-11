<template>
  <div>
    <input v-model="addItemName">
    <button v-on:click="onAdd()">Add</button>

    <ul class="todos">
      <li v-bind:key="item.id" v-for="item in todoItems" v-on:click="onEditTodo(item)">
        <span class="badge">{{item.id}}</span>
        {{item.name}}
        <button v-on:click="onDelete(item.id)" style="float: right;">Delete</button>
      </li>
    </ul>
    <div v-if="isEditVisible">
      <fieldset class="editTodo">
        <legend>{{selectedTodo.name.toUpperCase()}} Details</legend>
        <div>
          <span>id:</span>
          {{selectedTodo.id}}
          Name:
          <input
            class="todos"
            v-model="selectedTodo.name"
          >
          <button v-on:click="onUpdate()">Update</button>
        </div>
      </fieldset>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",

  data() {
    return {
      todo: "Take a break",
      selectedTodo: { id: 0, name: "" },
      isEditVisible: false,
      todoItems: [
        { id: 1, name: "Go to the shopping" },
        { id: 2, name: "Feed the cat" },
        { id: 3, name: "Walk the dog" },
        { id: 4, name: "Buy gas" },
        { id: 5, name: "Take a break" },
        { id: 6, name: "Call mommy" }
      ]
    };
  },

  methods: {
    onAdd() {
      this.todoItems.push({
        id: this.todoItems.length + 1,
        name: this.addItemName
      }),
        (this.addItemName = "");
    },
    onUpdate() {
      let findTodoIndex = this.todoItems.findIndex(
        t => t.id === this.selectedTodo.id
      );
      if (findTodoIndex) {
        this.todoItems[findTodoIndex].name = this.selectedTodo.name;
      }
    },

    onDelete(id) {
      this.todoItems = this.todoItems.filter(t => t.id !== id);
    },

    onEditTodo(item) {
      console.log("Name " + item.name);
      console.dir(this.selectedTodo);
      this.selectedTodo = { id: item.id, name: item.name };
      this.isEditVisible = true;
    }
  }
};
</script>

<style>
</style