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
  min-width: $todo-min-width;
  min-height: 100vh;
  padding-top: 50px;
  padding-bottom: 100px;
}
</style>
