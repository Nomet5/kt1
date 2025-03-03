<template>
  <div>
    <AddForm @addTodo="addTodo" />
    <TodoList
      :todos="todos"
      :deleteTodoByid="deleteTodoByid"
      :changeTodos="changeTodos"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import AddForm from './components/AddForm.vue';
import TodoList from './components/TodoList.vue';

const startTodos = [
  { id: 1, title: 'Помыть руки', completed: true },
  { id: 2, title: 'Сделать зарядку', completed: false },
  { id: 3, title: 'Наконец изучить React', completed: true },
];

const todos = ref(startTodos);

function deleteTodoByid(id) {
  todos.value = todos.value.filter((todo) => todo.id !== id);
}

function changeTodos(id) {
  todos.value = todos.value.map((todo) => {
    if (todo.id === id) {
      return { ...todo, completed: !todo.completed };
    }
    return todo;
  });
}

function addTodo(title) {
  const newTodo = {
    id: Date.now(),
    title,
    completed: false,
  };
  todos.value = [...todos.value, newTodo];
}


</script>