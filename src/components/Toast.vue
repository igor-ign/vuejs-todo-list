<script setup lang="ts">
import { ToastType } from '@/types/toast'

interface Props {
  type: ToastType
  message: string
}

const { type, message } = defineProps<Props>()
</script>

<template>
  <div class="toast-container" :class="type">
    <span>{{ message }}</span>
  </div>
</template>

<style>
.toast-container {
  height: 80px;
  position: fixed;
  right: 10px;
  top: 10px;
  width: 300px;
  border-radius: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.error {
  background-color: var(--error);
  color: var(--secondary);
}

.success {
  background-color: var(--success);
  color: var(--primary);
}
</style>
