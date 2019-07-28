<template>
  <article class="todoList">
    <h3 class="todoList__title">To Do List</h3>
    <p class="todoList__subtitle">Things I have to get done today:</p>
    <ToDoList :todo="todoByStatus" @removeItemEvent="removeItem" />
    <p v-if="!todo.length" class="todoList__empty">Your todo list is empty.</p>
    <ToDoToggleButton v-if="todo.length" @sortButtonChanged="changeSortButtonStatus" />
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
        { label: "Learn Vue.js", done: false },
        { label: "Buy eggs", done: false }
      ],
      isSortButtonActive: false
    };
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
    }
  },
  computed: {
    todoByStatus: function() {
      if (!this.isSortButtonActive) {
        return this.todo;
      } else {
        const doneList = this.todo.filter(element => element.done);
        const notDoneList = this.todo.filter(element => !element.done);
        return [...notDoneList, ...doneList];
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
  font-family: $main-font;
  color: $text-color;
  background: $brand-color-1;
  text-align: left;
  box-shadow: -1rem -1rem 0px 0px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  min-width: $todo-min-width;
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

.todoList__empty {
  margin-top: 2rem;
  margin-bottom: 2rem;
  font-size: 0.9rem;
  font-style: italic;
}
</style>