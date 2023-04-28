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
        <div class="todo-item">
          <input type="checkbox" v-model="todo.done" />
          <span :class="{ done: todo.done }">{{ todo.text }}</span>
          <button class="remove-btn" @click="removeTodo(index)">Remove</button>
        </div>
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
.todo-item {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.remove-btn {
  margin-left: 10px;
  background-color: #ff6347;
  border: none;
  color: #fff;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.2s;
}

.remove-btn:hover {
  background-color: #ff4438;
}
.done {
  text-decoration: line-through;
  color: #777;
}
</style>
