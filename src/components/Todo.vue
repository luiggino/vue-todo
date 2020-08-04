<template>
    <b-row>
        <b-col cols="4"></b-col>
      <b-col cols="4">
          <div class="text-left shadow-none"
                  v-bind:class="{ completed }"
                  v-on:click="$emit('toggle-todo')"
                  v-if="!isEditing">
              <span>{{ title }}</span>
          </div>
          <b-form v-else @submit.prevent="finishEditing()">
              <b-input
                type="text"
                v-model="newTodoTitle"
                v-on:blur="finishEditing()"
                ref="newTodo">
              </b-input>
          </b-form>
      </b-col>
      <b-col cols="4">
        <b-button @click="startEditing()" variant="outline-secondary" class="mx-1">
              <font-awesome-icon :icon="['fas', 'edit']" />
        </b-button>
        <b-button @click="$emit('delete-todo')" variant="danger">
              <font-awesome-icon :icon="['fas', 'trash']" />
        </b-button>
      </b-col>
    </b-row>
</template>

<script>
export default {
  name: "Todo",
    data() {
      return {
          isEditing: false,
          newTodoTitle: ""
      }
    },
  props: {
      id: String,
      title: String,
      completed: Boolean
  },
  methods: {
    startEditing() {
        if (this.isEditing) {
            this.finishEditing();
        } else {
            this.newTodoTitle = this.title;
            this.isEditing = true;
            this.$nextTick(() => this.$refs.newTodo.focus());
        }
      },
      finishEditing() {
        this.isEditing = false;
        this.$emit("edit-todo", this.newTodoTitle)
      }
  }
};
</script>

<style lang="scss" scoped>
.completed {
  text-decoration: line-through;
}
</style>
