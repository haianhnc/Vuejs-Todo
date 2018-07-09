<template>
   <div class='ui centered card'>
    <!-- Todo shown when we are not in editing mode. -->
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ todo.title }}
      </div>
      <div class='meta'>
          {{ todo.project }}
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
      </div>
    </div>
    <div v-show="isEditing">
      <div class="ui-form">
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
            Close X
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
  },
};
</script>

