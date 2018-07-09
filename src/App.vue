<template>
  <div id="app">
    <todo-list v-bind:todos="todos"/>
  </div>
</template>

<script>
import TodoList from './components/TodoList';

export default {
  name: 'App',
  components: {
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
