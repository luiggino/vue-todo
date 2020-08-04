<template>
  <b-container fluid class="text-center">
    <b-row>
      <b-col class="well well-sm text-center">
        <h2 >{{ listName }}</h2>
      </b-col>
    </b-row>
    <b-row>
        <AddTodo v-on:add-todo="addTodo" />
    </b-row>
    <b-row>
        <Todo
                v-for="todo in todos"
                v-bind:key="todo.id"
                v-bind:title="todo.title"
                v-bind:completed="todo.completed"
                v-on:edit-todo="editTodo(todo, $event)"
                v-on:delete-todo="deleteTodo(todo.id)"
        />
    </b-row>
  </b-container>
</template>

<script>
import Todo from "./Todo";
import AddTodo from "./AddTodo";

export default {
  name: "Todos",
  components: {
    Todo,
    AddTodo
  },
  props: {
    listName: String,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Go workout",
          completed: false
        },
        {
          id: 2,
          title: "Do laundry",
          completed: false
        },
        {
          id: 3,
          title: "Cook food",
          completed: false
        },
        {
          id: 4,
          title: "Clean up room",
          completed: false
        },
        {
          i: 5,
          title: "Finish work",
          completed: false
        }
      ]
    };
  },
  methods: {
    addTodo(newTodoObj) {
      this.todos = [...this.todos, newTodoObj];
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(t => t.id !== todoId);
    },
    editTodo(todo, newTodoTitle) {
      todo.title = newTodoTitle;
    }
  }
};
</script>

<style scoped></style>
