<template>
  <div>
    <h2>Todo list here!</h2>
    <ul>
      <li v-for="todo in todos" :key="todo.id">{{ todo.task }}</li>
    </ul>
  </div>
</template>

<script>
const axios = require('axios');

export default {
  data() {
    return {
      todos: [],
    };
  },
  created() {
    axios
      .get('http://localhost:8000/todo/')
      .then((response) => {
        this.todos = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style>
</style>
