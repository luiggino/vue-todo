<template>
  <div id="app">
    <Todos list-name="My List" />
  </div>
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "App",
  components: {
    Todos
  },
};
</script>

<style lang="scss">
  @import "./styles/custom.scss";
  @import '../node_modules/bootstrap/scss/bootstrap';
  @import '../node_modules/bootstrap-vue/src/index.scss';
</style>
