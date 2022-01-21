<template>
  <li class="list-group-item">
    <div class="row">
      <div class="todo-container-title">
        <div class="todo-title" v-on:click="activateInEditMode" v-show="!isEditing" >
          <!-- display the todo's title -->
        </div>
        <form v-show="isEditing" v-on:submit.prevent="deActivateInEditMode">
          <div class="form-group">
            <!-- add an input to edit the todo's title -->
          </div>
        </form>
      </div>
      <div class="todo-infos">
        <span class="btn btn-default todo-rm-btn" v-on:click="removeTodo(todo)">remove</span>
        <span class="bg-success todo-status">Done</span> <!-- display this span only if the todo is done -->
        <span class="bg-danger todo-status">Not Done</span> <!-- display this span only if the todo is not finished -->
        <input v-model="todo.done" type="checkbox"> <!-- add a checkbox to toggle the todo's done property -->
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
      // send a signal "remove-todo" with todo as parameter
    }
  }
}
</script>

<style scoped>
.todo-title {
  cursor: pointer;
  padding: 6px;
}

.todo-rm-btn {
  background-color: lightgray;
  padding: 3px;
  border-radius: 2px;
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

