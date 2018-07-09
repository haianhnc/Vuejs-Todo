<template>
  <div id="app">
    <create-todo @create-todo="createTodo" />
    <todo-list v-bind:todos="todos"/>
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import createTodo from './components/CreateTodo';

export default {
  name: 'App',
  components: {
    createTodo,
    TodoList,
  },

  data() {
    return {
      todos: [{
        title: 'todoA',
        project: 'projectA',
        done: false,
      },
      {
        title: 'todoB',
        project: 'projectB',
        done: true,
      },
      {
        title: 'todoC',
        project: 'projectC',
        done: false,
      },
      {
        title: 'todoD',
        project: 'projectA',
        done: true,
      }],
    };
  },

  methods: {
    createTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
