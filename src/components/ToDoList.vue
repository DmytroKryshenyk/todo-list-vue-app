<template>
  <ul>
    <li class="todoList__list" v-for="item in todo" v-bind:key="item.id">{{item.label}}</li>
  </ul>
</template> 

<script>
export default {
  name: "ToDoList",
  props: ["todo"]
}

</script>

