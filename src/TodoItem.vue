<script setup>

const emit = defineEmits(['remove-todo'])

const props = defineProps({
  todo: {
    type: Object,
    required: true
  }
})

function handleRemove(todoId) {
  emit('remove-todo', todoId);
}
</script>

<template>
  <li>
    <input type="checkbox" v-model="todo.completed">
    <span :class="{ done: todo.completed }">{{ todo.id }} - {{ todo.text }}</span>
    <button @click="handleRemove(todo.id)">X</button>
  </li>
</template>
