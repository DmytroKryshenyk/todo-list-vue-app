<template>
  <article class="todoList">
    <h3 class="todoList__title">Todo List</h3>
    <p class="todoList__subtitle">Things I have to get done today:</p>
    <ToDoList :todo="sortedTodo" @removeItemEvent="removeItem" />
    <ToDoToggleButton @sortButtonChanged="changeSortButtonStatus" />
    <ToDoForm @newItem="addNewTodo" />
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
        { label: "Meditation", done: true },
        { label: "Wash car", done: true },
        { label: "Read New Book", done: false },
        { label: "Learn Vue.js", done: false },
        { label: "Buy eggs", done: false }
      ],
      sortedTodo: [],
      isSortButtonActive: false
    };
  },
  beforeMount() {
    this.updateSortedTodo();
  },
  methods: {
    removeItem(label) {
      const index = this.todo.findIndex(current => current.label === label);
      this.todo.splice(index, 1);
    },

    addNewTodo(newTodo) {
      const newTodoObject = {
        label: newTodo[0].toUpperCase() + newTodo.substring(1),
        done: false
      };
      this.todo.unshift(newTodoObject);
    },

    changeSortButtonStatus(status) {
      this.isSortButtonActive = status;
      this.updateSortedTodo();
    },

    updateSortedTodo() {
      if (this.isSortButtonActive) {
        let doneList = this.todo.filter(element => element.done);
        let notDoneList = this.todo.filter(element => !element.done);
        this.sortedTodo = [...notDoneList, ...doneList];
      } else {
        this.sortedTodo = this.todo;
      }
    }
  }
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
  box-shadow: -1rem -1rem 0px 0px rgba(0, 0, 0, 0.1);
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