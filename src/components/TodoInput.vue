<script setup lang="ts">
import { ref } from 'vue';

const text = ref<string>('');
const emit = defineEmits<{ (e: 'add', text: string): void }>();
const emitAddTodo = () => {
  if (!text.value.trim()) return;
  emit('add', text.value);
  text.value = '';
};
</script>

<template>
  <input
    type="text"
    class="todo-input"
    v-model="text"
    @keyup.enter="emitAddTodo"
  />
  <button class="add-button" @click="emitAddTodo">추가</button>
</template>

<style scoped>
.todo-input {
  width: 100%;
  max-width: 300px;
  padding: 15px;
  border: none;
  border-radius: 4px;
  margin-bottom: 10px;
  font-size: 18px;
}

.add-button {
  margin-left: 10px;
}
</style>
