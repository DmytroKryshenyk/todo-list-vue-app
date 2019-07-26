<template>
  <article class="todoList">
    <h3 class="todoList__title">Todo List</h3>
    <p class="todoList__subtitle">Today i need To:</p>
    <ToDoList :todo="todo" />
    <ToDoToggleButton />
    <ToDoForm />
  </article>
</template>

<script>
import ToDoList from "./ToDoList.vue";
import ToDoToggleButton from "./ToDoToggleButton.vue";
import ToDoForm from "./ToDOForm.vue";

export default {
  name: "ToDo",
  components: {
    ToDoList,
    ToDoToggleButton,
    ToDoForm
  },
  data() {
    return {
      todo: [
        { id: 1, label: "GO to the GYM ", done: true },
        { id: 2, label: "Read New Book", done: false },
        { id: 3, label: "Meditation", done: false }
      ]
    };
  },
  methods: {}
};
</script>


<style lang="scss" scoped>
</style>

