<script setup>
import { reactive, ref, computed } from 'vue'
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue'

// Give each todo a unique id
let id = 0

const todos = reactive([
  { id: id++, text: 'Learn HTML', completed: false },
  { id: id++, text: 'Learn JavaScript', completed: true },
  { id: id++, text: 'Learn Vue', completed: false }
])


function addTodo(todoText) {
  if (todoText.trim()) {
    todos.push({ id: id++, text: todoText.trim(), completed: false })
  }
}

function removeTodo(todoId) {
  const index = todos.findIndex(todo => todo.id === todoId)
  if (index !== -1) {
    todos.splice(index, 1)
  }
}
</script>

<template>
  <div>
    <TodoForm @add-todo="addTodo" />
    <br/>
    <TodoList :todos="todos" @remove-todo="removeTodo" />
  </div>
</template>
