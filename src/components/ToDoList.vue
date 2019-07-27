<template>
  <ul class="todoList__list">
    <li class="todoList__item" v-for="item in todo" v-bind:key="item.id">
      <span class="todoList__text" :class="{'todoList__text--done': item.done }">{{item.label}}</span>

      <form class="todoList__actions">
        <label class="todoList__done">
          <input class="todoList__done-input" v-model="item.done" type="checkbox" />
          <span class="todoList__done-span"></span>
        </label>
        <button
          class="todoList__remove"
          @click="emitRemoveItem(item.label)"
          type="button"
          aria-label="Delete"
          title="Delete"
        ></button>
      </form>
    </li>
  </ul>
</template> 

<script>
export default {
  name: "ToDoList",
  props: ["todo"],
  methods: {
    emitRemoveItem(label) {
      this.$emit("removeItemEvent", label);
    }
  }
};
</script>

<style lang="scss" scoped>
.todoList__list {
  padding: 0;
  margin-bottom: 1rem;
}

.todoList__item {
  display: flex;
  justify-content: space-between;
  padding-top: 0.7rem;
  padding-bottom: 0.7rem;

  margin-bottom: 0.1rem;
  position: relative;
  z-index: 1;

  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    width: calc(100% + 2 * #{$main-padding});
    height: 100%;
    background: rgba(255, 255, 255, 0.15);
    z-index: -1;
  }
}

.todoList__text--done {
  position: relative;
  opacity: 0.5;

  &:after {
    content: "";
    width: calc(100% + 1rem);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%);
    background-color: $text-color;
    height: 0.0625rem;
  }
}

.todoList__actions {
  display: inline-block;
  margin-left: 1rem;
}

.todoList__done,
.todoList__remove {
  vertical-align: middle;
}

.todoList__done {
  display: inline-block;
  margin-right: 0.5rem;
  position: relative;
  font-size: 0;
}

.todoList__done-input {
  opacity: 0;
  height: 1rem;
  width: 1rem;

  &:checked + .todoList__done-span {
    background: url(../assets/check-solid.svg);
    background-size: cover;
  }
}

.todoList__done-span {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border: 0.1rem solid #ffffff;
  border-radius: 20%;
}

.todoList__remove {
  border: none;
  padding: 0;
  height: 1rem;
  width: 1rem;
  background: url(../assets/trash-solid.svg) no-repeat;
  z-index: 2;
}
</style>


