<template>
  <div class="sub-container">
    <h2 class="sub-title">
      Total Todo Count <span class = "badge"> {{ todos.length }} </span>
    </h2>
    <ul class="list-group">
      <todo v-on:remove-todo="removeTodo" v-for="todo in todos" :todo.sync="todo" key="todo"></todo>
    </ul>
  </div>
</template>

<script type = "text/javascript" >

import Todo from './Todo.vue';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    removeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    }
  }
};
</script>

<style scoped>
.sub-title {
  padding: 5px 10px;
}

.sub-container {
  display: flex;
  flex-direction: column;
  margin-left: 10px;
}

.list-group {
  max-width: 100%;
  width: 100%;
  padding: 0;
  margin: 0;
}

ul {
  list-style-type: none;
  max-width: 50%;
  width: 100%;
}
</style>
