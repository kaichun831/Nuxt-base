<template>
  <div>
    <p>Bounce</p>
    <ul>
      <li v-for="todo in todos" :key="todo">
        <input type="checkbox" :checked="todo.done" @change="toggle(todo)" />
        <span>{{ todo.text }}</span>
      </li>
      <li>
        <input placeholder="What needs to be done?" @keyup.enter="addTodo" />
      </li>
    </ul>
  </div>
</template>
<script>
import { mapMutations } from "vuex";
export default {
  //   layout: "default",
  transition: "slide-bottom",
  computed: {
    todos() {
      return this.$store.state.todos.list;
    },
  },
  methods: {
    addTodo(e) {
      this.$store.commit("todos/add", e.target.value);
      e.target.value = "";
    },
    ...mapMutations({
      toggle: "todos/toggle",
    }),
  },
};
</script>