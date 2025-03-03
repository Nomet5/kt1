<template>
    <div>
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :id="todo.id"
        :title="todo.title"
        :completed="todo.completed"
        :deleteTodoByid="deleteTodoByid"
        :changeTodos="changeTodos"
      />
    </div>
  </template>
  
  <script setup>
  import TodoItem from './TodoItem.vue';
  
  const props = defineProps({
    todos: Array,
    deleteTodoByid: Function,
    changeTodos: Function,
  });
  </script>