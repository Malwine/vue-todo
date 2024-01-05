<template>
  <div class="container container-fix">
    <div class="row">
      <div class="col-12">
        <p class="display-4">
          Vue Todos
        </p>
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-lg-12">
        <NewTodo @on-addtodo="addTodo($event)"/>
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <SingleTodo v-for="(todo, index) in todos" 
          :key="index" 
          :text="todo.text"
          :completed="todo.completed"
          @on-delete="deleteTodo(todo)"
          @on-toggle="toggleTodo(todo)"
          @on-edit="editTodo(todo,$event)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import SingleTodo from "./SingleTodo.vue";
import NewTodo from "./NewTodo";
export default {
  components: {
    SingleTodo,
    NewTodo,
  },
  data() {
    return {
      todos: [
        { id: 1, text: "Learn Vue", completed: true },
        { id: 2, text: "Learn many things with Hitesh", completed: false },
        { id: 3, text: "Have fun", completed: false },
      ]
    };
  },
  methods: {
    addTodo(newTodo){
      this.todos.push({
        text: newTodo, completed: false});
    },
    toggleTodo(todo){
      todo.completed = !todo.completed;
    }, 
    editTodo(todo, newText){
      todo.text = newText;
    }, 
    deleteTodo(deleteTodo){
      this.todos = this.todos.filter(todo => todo !== deleteTodo)
    }
  },
};
</script>

<style>
.container-fix {
  margin-top: 50px;
}
</style>