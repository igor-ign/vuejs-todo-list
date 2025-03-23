<script setup lang="ts">
import { TodoListItem } from './types/todo-list-item'
import TodoList from './components/TodoList.vue'
import { ref } from 'vue'

let todoList = ref<TodoListItem[]>([])
let todoListItemTitle = ref<string>('')

function handleAddTodoListItem() {
  if (todoListItemTitle.value.length === 0) return

  todoList.value.push({
    title: todoListItemTitle.value,
    isDone: false,
  })

  todoListItemTitle.value = ''
}
</script>

<template>
  <main class="main-page">
    <div class="content container">
      <form @submit.prevent="handleAddTodoListItem" class="todo-list-form">
        <input type="text" v-model="todoListItemTitle" class="form-input" />
        <button class="form-button">Add Item</button>
      </form>

      <TodoList :list="todoList" />
    </div>
  </main>
</template>

<style scoped>
.main-page {
  background-color: var(--primary);
  height: 100vh;
  width: 100vw;
}

.content {
  padding-top: 60px;
}

.todo-list-form {
  align-items: center;
  background-color: var(--tertiary);
  border-radius: 10px;
  display: flex;
  gap: 30px;
  height: 150px;
  height: 80px;
  justify-content: center;
  margin: 0 auto;
  padding: 30px;
  width: 370px;
}

.form-input {
  background-color: var(--primary-light);
  border-radius: 6px;
  border: none;
  color: var(--secondary);
  height: 30px;
}

.form-button {
  background-color: var(--quaternary);
  border-radius: 6px;
  border: none;
  cursor: pointer;
  height: 30px;
  width: 80px;
}

.form-button:hover {
  background-color: var(--quaternary-hover);
}
</style>
