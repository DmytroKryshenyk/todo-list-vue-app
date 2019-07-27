<template>
  <form class="todoList__form" @submit.prevent="submited">
    <label class="todoList__label" for="newitem">Add to the todo list</label>
    <input class="todoList__input" v-model="newItem" type="text" name="newitem" id="newitem" />
    <button class="todoList__submit" type="submit">Add item</button>
  </form>
</template>

<script>
export default {
  name: "ToDoForm",
  data() {
    return { newItem: "" };
  },
  methods: {
    submited(event) {
      this.$emit("newItem", this.newItem);
    }
  }
};
</script>

<style lang="scss" scoped>
.todoList__form {
  display: flex;
  flex-wrap: wrap;
}

.todoList__label {
  flex-basis: 100%;
  font-size: 1.4rem;
  margin-bottom: 0.3rem;
}

.todoList__input {
  height: 3rem;
  flex: 1 1;
  padding: 0.5rem;
  color: #7c7c7c;
}

.todoList__submit {
  height: 3rem;
  padding: 0 1.5rem;
  background: $brand-color-2;
  color: $text-color;
  text-transform: uppercase;
  border: none;
  margin-left: 0.3em;
}
</style>


