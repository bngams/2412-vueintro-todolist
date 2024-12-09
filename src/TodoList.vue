<script setup>
import { ref, computed } from 'vue'
import TodoItem from './TodoItem.vue';

const props = defineProps({
  todos: {
    type: Array,
    required: true
  }
})

const emit = defineEmits(['remove-todo'])

function handleRemove(todoId) {
  emit('remove-todo', todoId)
}

// Manage visibility of completed todos
const hideCompleted = ref(false)

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? props.todos.filter(todo => !todo.completed)
    : props.todos
})
</script>

<template>
  <div>
    Filters : <button @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Show all' : 'Hide completed' }}
    </button>
    <ul>
      <TodoItem v-for="todo in filteredTodos" :todo="todo" :key="todo.id" @remove-todo="handleRemove" />
    </ul>
  </div>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
