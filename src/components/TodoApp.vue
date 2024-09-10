<template>
  <div class="flex items-center justify-center min-h-screen bg-gray-100">
    <div class="w-full max-w-md p-6 mx-auto bg-white rounded-lg">
      <h1 class="text-2xl font-semibold text-center text-gray-900">Todo App</h1>
      <form @submit.prevent="addTodo">
        <div class="flex items-center mt-4">
          <input
            v-model="newTodo"
            type="text"
            class="w-full px-4 py-2 mr-2 text-gray-700 bg-gray-200 rounded-lg focus:outline-none"
            placeholder="Add a new todo..."
          />
          <button
            type="submit"
            class="px-4 py-2 text-white bg-blue-500 rounded-lg hover:bg-blue-400 focus:outline-none"
          >
            Add
          </button>
        </div>
        <ul class="mt-8">
          <li
            v-for="(todo, index) in todos"
            :key="index"
            class="flex items-center justify-between p-4 mb-2 bg-gray-200 rounded-lg"
          >
            <span class="text-gray-900">{{ todo }}</span>
            <button
              @click="removeTodo(index)"
              class="p-3 text-sm text-white bg-red-500 rounded-lg hover:bg-red-400 focus:outline-none"
            >
              Delete
            </button>
          </li>
        </ul>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const todos = ref([
  "Create a new project",
  "Add a new feature",
  "Fix the bugs",
]);
const newTodo = ref("");

console.log(newTodo.value);

const addTodo = () => {
  if (newTodo.value.trim() !== "") {
    todos.value.push(newTodo.value);
    newTodo.value = "";
  }
};

const removeTodo = (index) => {
  todos.value.splice(index, 1);
};
</script>
