<script setup lang="ts">
import { TodoListItem } from '../types/todo-list-item'

interface Props {
  list: TodoListItem[]
}

const { list } = defineProps<Props>()
</script>

<template>
  <ul class="todo-list">
    <li v-for="({ isDone, title }, index) in list" class="todo-item">
      <span class="todo-item-index">{{ index + 1 }}</span>
      <div class="todo-item-content">
        <span class="todo-item-title">{{ title }}</span>
        <input type="checkbox" :checked="isDone" class="todo-item-checkbox" />
      </div>
    </li>
  </ul>
</template>

<style>
.todo-list {
  align-items: center;
  display: flex;
  flex-direction: column;
  gap: 10px;
  justify-content: flex-start;
  margin: 30px auto;
  max-height: 300px;
  overflow-y: auto;
  padding-top: 20px;
  width: 400px;
}

.todo-item {
  align-items: center;
  background-color: var(--tertiary);
  border-radius: 6px;
  color: var(--secondary);
  display: flex;
  gap: 10px;
  height: 50px;
  justify-content: space-between;
  padding: 14px;
  width: 370px;
}

.todo-item-index {
  font-size: 1.3rem;
  font-weight: bold;
}

.todo-item-content {
  align-items: center;
  display: flex;
  font-weight: 400;
  gap: 20px;
  justify-content: space-between;
}

.todo-item-checkbox {
  border-radius: 10px;
  height: 20px;
  width: 20px;
}
</style>
