<script setup lang="ts">
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import { ITodo } from './components/TodoItem.vue';
import { ref, watch } from 'vue';

const todos = ref<ITodo[]>([]);

const addTodo = (text: string) => {
  todos.value.push({ id: Date.now(), text, completed: false });
};

const toggleTodo = (id: number) => {
  todos.value = todos.value.map((todo) =>
    id === todo.id ? { ...todo, completed: !todo.completed } : todo
  );
};
const removeTodo = (id: number) => {
  todos.value = todos.value.filter((todo) => id !== todo.id);
};

watch(todos, (oldTodos, newTodos) => {
  console.log(todos.value);
});
</script>

<template>
  <div class="container">
    <h1>TODO List</h1>
    <TodoInput @add="addTodo" />
    <TodoList :todos="todos" @toggle="toggleTodo" @remove="removeTodo" />
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

h1 {
  text-align: center;
}
</style>
