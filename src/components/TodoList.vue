<script setup lang="ts">
import TodoItem from './TodoItem.vue';
import { toRefs } from 'vue';
import { ITodo } from './TodoItem.vue';

interface ITodoList {
  todos: ITodo[];
}

const props = defineProps<ITodoList>();
const { todos } = toRefs(props);

const emit = defineEmits<{
  (e: 'toggle', id: number): void;
  (e: 'remove', id: number): void;
}>();
</script>

<template>
  <ul>
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle="emit('toggle', todo.id)"
      @remove="emit('remove', todo.id)"
    />
  </ul>
</template>

<style scoped></style>
