<template>
  <div id="app">
    <h1>Список дел до конца года</h1>
    <hr>

    <router-view />
    </div>
</template>

<script>

import ToDoList from '@/components/ToDoList'
import AddTodo from '@/components/AddTodo'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'Выучить JS', completed: false},
        {id: 2, title: 'Выучить Vue', completed: false},
        {id: 3, title: 'Найти работу', completed: false},
      ]
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
    .then(response => response.json())
    .then(json => {
      this.todos = json
    })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id != id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    },
  },
  components: {
    ToDoList,
    AddTodo,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
