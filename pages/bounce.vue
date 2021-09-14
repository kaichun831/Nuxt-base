<template>
  <div>
    <p>Bounce</p>
    <!-- <ul>
      <li v-for="todo in todos" :key="todo.text">
        <input :checked="todo.done" @change="toggle(todo)" type="checkbox" />
        <span :class="{ done: todo.done }">{{ todo.text }}</span>
      </li>
      <li>
        <input @keyup.enter="addTodo" placeholder="What needs to be done?" />
      </li>
    </ul> -->
    <!-- <p>{{ todos }}</p> -->
  </div>
</template>
<script>
import { mapMutations } from "vuex";
export default {
  //   layout: "default",
  transition: "slide-bottom",
  computed: {
    todos() {
      console.log(this.$store);
      return this.$store.state.todo.state;
    },
  },
  methods: {
    addTodo(event) {
      this.$store.commit("todos/add", event.target.value);
      event.target.value = "";
    },
    ...mapMutations({
      toggle: "todos/toggle",
    }),
    removeTodo(todo) {
      this.$store.commit("todos/remove", todo);
    },
  },
};
</script>