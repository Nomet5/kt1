<template>
    <div
      class="todo_card"
      :style="{ backgroundColor: completed ? 'green' : 'red' }"
      @dblclick="deleteTodo"
      @click="changeTodo"
    >
      <h2>{{ title }}</h2>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    title: String,
    completed: Boolean,
    id: Number,
    deleteTodoByid: Function,
    changeTodos: Function,
  });
  
  function deleteTodo() {
    if (typeof props.deleteTodoByid === 'function') {
      props.deleteTodoByid(props.id);
    } else {
      console.error('deleteTodoByid is not a function');
    }
  }
  
  function changeTodo() {
    if (typeof props.changeTodos === 'function') {
      props.changeTodos(props.id);
    } else {
      console.error('changeTodos is not a function');
    }
  }
  </script>
  
  <style scoped>
  .todo_card {
    display: flex;
    flex-direction: column;
    padding: 10px;
    margin: 20px 170px;
    outline: 2px solid black;
    box-shadow: 5px 5px 10px black;
  }
  </style>  