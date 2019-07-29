<template>
  <div id="app">
    <ToDo />
  </div>
</template>

<script>
import ToDo from "./components/ToDo.vue";

export default {
  name: "App",
  components: {
    ToDo
  }
};
</script>

<style lang="scss">
#app {
  text-align: center;
  background: $brand-color-3;
  min-height: 100vh;
  min-width: $todo-min-width;
  padding-top: 100px;
  padding-bottom: 100px;
}
</style>
