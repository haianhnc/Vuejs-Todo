<template>
   <div class='ui centered card'>
    <!-- Todo shown when we are not in editing mode. -->
    <div class="content" v-show="!isEditing">
      <div class='header' @click="completedTodo(todo)">
          {{ todo.title }}
      </div>
      <div class='meta'>
          {{ todo.project }}
      </div>
      <label for="completed" @click="changeTodoStatus(todo)">
        {{ todo.done ? 'Completed' : 'Pending' }}
      </label>
      <div class='extra content'>
          <span class='right floated edit icon' @click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class="right floated trash icon" @click="deleteTodo(todo)">
          <i class="trash icon"></i>
        </span>
      </div>
    </div>
    <div v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label for="todo title">Title</label>
          <input type="text" v-model="todo.title" />
        </div>
        <div class="field">
          <label for="project">Project</label>
          <input type="text" v-model="todo.project" />
        </div>
        <div class="ui two button attached buttons">
          <button class='ui basic blue button' @click="hideForm">
            Save Me
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-show="!isEditing && todo.done" disabled>
        Completed
    </div>
    <div class='ui bottom attached red basic button' v-show="!isEditing && !todo.done">
        Pending
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    completedTodo(todo) {
      this.$emit('completed-todo', todo);
    },
    changeTodoStatus(todo) {
      this.$emit('change-todo-status', todo);
    },
  },
};
</script>

