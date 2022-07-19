<template>
  <div id="add-container">
    <form @submit="addTodo">
      <input type="text" v-model="title" />
    </form>
  </div>
</template>

<script>
import { v4 } from "uuid";

export default {
  name: "TodoAdd",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();

      const newTodo = {
        id: v4(),
        title: this.title,
        completed: false,
      };

      this.title = "";
      this.$emit("add-todo", newTodo);
    },
  },
};
</script>

<style>
#add-container {
  padding: 10px;
}

input {
  padding: 10px;
  outline: none;
  border: solid 1px #ccc;
  width: 100%;
}
</style>
