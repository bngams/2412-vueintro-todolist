<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add-todo'])

const newTodo = ref('')

function submitForm() {
  if (newTodo.value.trim()) {
    // Emit the add-todo event with the new todo text
    emit('add-todo', newTodo.value)
    newTodo.value = '' // Clear the input field
  }
}
</script>

<template>
  <form @submit.prevent="submitForm">
    <input v-model="newTodo" required placeholder="New todo" />
    <button type="submit">Add Todo</button>
  </form>
</template>
