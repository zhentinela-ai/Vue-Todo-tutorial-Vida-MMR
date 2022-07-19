<template>
  <div class="todo-container" v-bind:class="{ completed: todo.completed }">
    <div class="todo-body">
      <input
        type="checkbox"
        v-bind:checked="todo.completed ? 'completed' : ''"
        v-on:change="checkTodo"
      />
      {{ todo.title }}
    </div>
    <div class="todo-actions">
      <button @click="$emit('delete-todo', todo.id)">Eliminar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    checkTodo() {
      // eslint-disable-next-line vue/no-mutating-props
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style>
.todo-container {
  display: flex;
  justify-content: space-between;
  padding: 0 0 5px 0;
  border-bottom: solid 1px #ccc;
  padding: 10px;
}

.todo-container:not(.completed):hover {
  background-color: #eee;
}

.completed {
  color: #ccc;
  text-decoration: line-through;
}

.completed .todo-body {
  text-decoration: line-through;
}

.completed .todo-body {
  text-decoration: line-through;
}

.todo-body,
.todo-actions {
  display: inline-block;
  vertical-align: top;
}

.todo-body {
  widows: 85%;
}

.todo-actions {
  padding: 0 10px;
  width: 15%;
}

button {
  border: none;
  border-radius: 3px;
  padding: 10px;
  background-color: #aaa;
  color: #222;
  /* float: left; */
}

button:hover {
  background-color: #da2020;
  color: #ddd;
  cursor: pointer;
}
</style>
