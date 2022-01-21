<template>
  <li class="list-group-item">
    <div class="row">
      <div class="todo-container-title">
        <div class="todo-title" v-on:click="activateInEditMode" v-show="!isEditing" >
          {{ todo.title }}
        </div>
        <form v-show="isEditing" v-on:submit.prevent="deActivateInEditMode" >
          <div class="form-group">
            <input v-model="todo.title" type="text" class="form-control" >
          </div>
        </form>
      </div>
      <div class="todo-infos">
        <span class="btn btn-default" v-on:click="removeTodo(todo)" style="background-color: lightgray; padding: 3px; border-radius: 2px">remove</span>
        <span v-if="todo.done" class="bg-success todo-status">Done</span>
        <span v-else="todo.done" class="bg-danger todo-status">Not Done</span>
        <input v-model="todo.done" type="checkbox">
      </div>
    </div>
  </li>
</template>

<script type="text/javascript">
export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false
    }
  },
  methods: {
    activateInEditMode() {
      this.isEditing = true
    },
    deActivateInEditMode() {
      this.isEditing = false
    },
    removeTodo (todo) {
      this.$emit('remove-todo', todo)
    }
  }
}
</script>

<style scoped>
.todo-title {
  cursor: pointer;
  padding: 6px;
}

.todo-infos {
  margin: 5px 0 10px 0;
}

.todo-container-title {
  width: 100%;
}

.todo-title:hover {
  background-color: #F1EDED;
}

.row {
  border: 2px solid lightgray;
  border-radius: 10px;
  margin-bottom: 10px;
}
</style>

