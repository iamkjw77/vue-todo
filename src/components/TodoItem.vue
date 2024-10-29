<script setup lang="ts">
import { toRefs } from 'vue';

export interface ITodo {
  id: number;
  text: string;
  completed: boolean;
}

const props = defineProps<{ todo: ITodo }>();
const { todo } = toRefs(props);
</script>

<template>
  <li class="todo-item">
    <div class="todo-item-container">
      <input type="checkbox" @change="$emit('toggle')" class="todo-checkbox" />
      <p :class="['todo-text', { completed: todo.completed }]">
        {{ todo.text }}
      </p>
    </div>
    <button @click="$emit('remove')">삭제</button>
  </li>
</template>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 10px;
  width: 100%;
  background-color: #ff95ef;
  border-radius: 5px;
  margin-bottom: 10px;
}

.todo-item-container {
  display: flex;
}

.todo-checkbox {
  width: 25px;
  margin-right: 10px;
}

.todo-text {
  font-size: 18px;
  font-weight: bold;
}

p.completed {
  text-decoration: line-through;
}
</style>
