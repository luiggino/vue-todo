<template>
  <b-col >
    <b-form @submit.prevent="addTodo" inline class="justify-content-center">
      <b-input-group>
        <b-form-input
                type="text"
                v-model="title"
                name="title"
                placeholder="Create a new to-do..."/>
        <b-input-group-append>
          <b-button type="submit" variant="primary">Add</b-button>
        </b-input-group-append>
      </b-input-group>
    </b-form>
  </b-col>

</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const newTodoObj = {
        id: uuidv4(),
        title: this.title,
        completed: false
      };

      this.$emit("add-todo", newTodoObj);
      this.title = "";
    }
  }
};
</script>

<style scoped></style>
