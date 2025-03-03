<template>
    <div class="input_elem">
      <input @keyup.enter="handleKeyUp" v-model="newTodoTitle" />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const emit = defineEmits(['addTodo']); // Используем defineEmits для передачи событий
  const newTodoTitle = ref('');
  
  function handleKeyUp(event) {
    if (event.key === 'Enter' && newTodoTitle.value.trim()) {
      emit('addTodo', newTodoTitle.value); // Передаем событие в родительский компонент
      newTodoTitle.value = '';
    }
  }
  </script>
  
  <style scoped>
  .input_elem {
    display: flex;
    justify-content: center;
    margin: 20px;
  }
  
  .input_elem > input {
    outline: 2px solid black;
    box-shadow: 5px 5px 10px black;
  }
  </style>