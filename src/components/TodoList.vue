<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo
      v-for="todo in todos"
      v-bind:todo="todo"
      v-bind:key="todo.index"
      @delete-todo="deleteTodo"
      @completed-todo="completedTodo"
      @change-todo-status="changeTodoStatus"
    >
    </todo>
  </div>
</template>

<script>
import Todo from './Todo';
import CreateTodo from './CreateTodo';

export default {
  props: ['todos'],
  components: {
    Todo,
    CreateTodo,
  },

  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    completedTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
    changeTodoStatus(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = !this.todos[todoIndex].done;
    },
  },
};
</script>

<style>
</style>
