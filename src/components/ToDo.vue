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
.todoList {
  display: inline-block;
  padding: $main-padding;
  padding-top: $main-top-padding;
  font-family: "Neucha", cursive;
  color: $text-color;
  background: $brand-color-1;
  text-align: left;
  box-shadow: -1rem -1rem 0px 0px rgba(0,0,0,0.1);
  overflow: hidden;
}

.todoList__title {
  font-size: 2.6rem;
  margin-bottom: 0.5rem;
}

.todoList__subtitle {
  font-size: 1rem;
  margin-bottom: 0.8rem;
  text-decoration: underline;
}
</style>

