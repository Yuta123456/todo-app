<template>
  <div class="home">
    <div id="todo-list-example">
      <form v-on:submit.prevent="addNewTodo">
        <label for="new-todo">Add a todo</label>
        <input
          v-model="newTodoText"
          id="new-todo"
          placeholder="E.g. Feed the cat"
        />
        <button>Add</button>
      </form>
      <ul>
        <todo-item
          v-for="(todo, index) in todos"
          :key="todo.id"
          :title="todo.title"
          @remove="todos.splice(index, 1)"
        ></todo-item>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import TodoItem from "@/components/TodoItem.vue";
// import { Options } from "vue-class-component";
export default defineComponent({
  name: "HomeView",
  components: {
    TodoItem,
  },
  setup() {
    const todos = ref([
      {
        id: 1,
        title: "Do the dishes",
      },
      {
        id: 2,
        title: "Take out the trash",
      },
      {
        id: 3,
        title: "Mow the lawn",
      },
    ]);
    const newTodoText = ref("");
    let nextTodoId = 4;
    const addNewTodo = () => {
      console.log("add fire");
      todos.value.push({
        id: nextTodoId,
        title: newTodoText.value,
      });
      nextTodoId++;
      newTodoText.value = "";
    };
    return {
      todos,
      newTodoText,
      addNewTodo,
    };
  },
});
</script>
