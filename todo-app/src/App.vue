<template>
  <div class="container" id="app">
    <div style="margin-right: 10px">
      <h1>Todo App</h1>
      <form v-on:submit.prevent="addNewTodo()">
        <div class="form-group">
          <input v-model="newTodoText" type="text" class="form-control" name="name" placeholder="Enter new Todo here">
        </div>
      </form>
    </div>
    <div>
      <todo-list v-bind:todos="todos"></todo-list>
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList
  },
  data() {
    return {
      newTodoText: "",
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false,
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false,
      }],
    };
  },
  methods: {
    addNewTodo() {
      if (this.newTodoText.length > 0) {
        this.todos.push({
          title: this.newTodoText,
          done: false
        })
        this.newTodoText = ''
      }
    }
  }
}
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

.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
</style>
