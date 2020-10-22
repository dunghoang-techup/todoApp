<template>
  <div class="container">
    <div class="row">
      <div class="col-12 py-5">
        <h1>{{ name }}</h1>
      </div>
      <div class="row mb-3">
        <create-todo v-on:on-new-todo="addTodo($event)" />
        <div class="clear-task">
          <h4>Clear all completed task</h4>
          <button class="btn btn-danger" v-on:click="deleteTodos()"><span class="fa fa-eraser"></span></button>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-sm-10 col-lg-6">
        <ul class="list-group">
          <toDo
              v-for="(todo, index) in todos"
              v-bind:key="index"
              v-bind:description="todo.description"
              v-bind:completed="todo.completed"
              v-on:on-toggle="toggleTodo(todo)"
              v-on:on-delete="deleteTodo(todo)"
              v-on:on-edit="editTodo(todo, $event)"
          />
        </ul>
      </div>
    </div>

  </div>
</template>

<script>
  import createTodo from "./createTodo";
  import toDo from "./toDo";
  export default {
    name: "toDoList",
    components: {createTodo, toDo},
    props: {
      name: String
    },
    data() {
      return {
        todos: [
          {description: "Do some exercise ", completed: false},
          {description: "Clean the house", completed: false},
          {description: "Feet the cat", completed: false}
        ],
      }
    },
    methods: {
      addTodo(newTodo) {
        this.todos.push({ description: newTodo, completed: false });
      },
      toggleTodo(e) {
        e.completed = !e.completed;
      },
      editTodo(e, newTodoDescription) {
        e.description = newTodoDescription;
      },
      deleteTodo(deleteEvent) {
        this.todos = this.todos.filter(todo => todo !== deleteEvent);
      },
      deleteTodos() {
        this.todos = this.todos.filter(todo => todo.completed === false)
      }
    }
  }
</script>

<style lang="scss" scoped>
.container {
  width: 100vh;
  position: relative;
  border: 1px double #333;
  border-radius: 20px;
  margin-bottom: 20px;
  .clear-task {
    display: flex;
    margin-top: 10px;
    button {
      margin-left: 10px;
    }
  }
  .row {
      display: flex;
      justify-content: center;
      flex-direction: row;
      padding: 5px;
  }
}
</style>