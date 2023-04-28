<template>
  <div>
    <h1>Todo List</h1>
    <form @submit.prevent="addTodo">
      <label for="todo">Add a new todo:</label>
      <input type="text" id="todo" v-model="newTodo" />
      <button type="submit">Add</button>
    </form>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input type="checkbox" v-model="todo.done" />
        <span :class="{ done: todo.done }">{{ todo.text }}</span>
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const todos = ref([
      { text: "Learn Vue 3", done: false },
      { text: "Build an app", done: false },
      { text: "Deploy to production", done: false },
    ]);

    const newTodo = ref("");

    function addTodo() {
      todos.value.push({ text: newTodo.value, done: false });
      newTodo.value = "";
    }

    function removeTodo(index) {
      todos.value.splice(index, 1);
    }

    return {
      todos,
      newTodo,
      addTodo,
      removeTodo,
    };
  },
};
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>
