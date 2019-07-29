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
  padding-top: 100px;
  background: $brand-color-3;
  height: 100vh; 
  min-width: $todo-min-width;

  
}
</style>
