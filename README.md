# Traitz Interns Vue.js Todo App

Welcome to the Traitz Interns Vue.js Todo App project! This project is designed to help interns learn the basics of Vue.js by building a simple Todo application.

## Prerequisites

Before you begin, ensure you have the following tools installed:

- [Node.js](https://nodejs.org/) (v14 or higher)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
- [Git](https://git-scm.com/)

## Installation

Follow these steps to clone and set up the project:

1. Clone the repository:
   ```sh
   git clone https://github.com/JuniorDCoder/Traitz-Interns-VueJs-TodoApp.git
   ```
2. Navigate to the project directory:
   `cd Traitz-Interns-VueJs-TodoApp`
3. Install the dependencies
   `npm install`
   or
   `yarn install`

## Project Structure

Here's a brief overview of the project structure:
Traitz-Interns-VueJs-TodoApp/
├── public/
├── src/
│ ├── assets/
│ ├── components/
│ │ └── TodoApp.vue
│ ├── App.vue
│ ├── main.js
├── .gitignore
├── package.json
├── README.md

## Detailed Code Explanation

./components/TodoApp.vue

```
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
              @click="deleteTodo(index)"
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

<script>
import { ref } from "vue";

export default {
  setup() {
    // Define a reactive variable to hold the list of todos
    const todos = ref(["Create a new project"]);

    // Define a reactive variable to hold the new todo input value
    const newTodo = ref("");

    // Function to add a new todo to the list
    const addTodo = () => {
      if (newTodo.value.trim()) {
        todos.value.push(newTodo.value);
        newTodo.value = "";
      }
    };

    // Function to delete a todo from the list by index
    const deleteTodo = (index) => {
      todos.value.splice(index, 1);
    };

    // Return the reactive variables and functions to make them available in the template
    return {
      todos,
      newTodo,
      addTodo,
      deleteTodo,
    };
  },
};
</script>
```

## Explanation

Template Section:

The outer div centers the content using Flexbox and sets a minimum height.
The inner div contains the Todo App UI, including a form for adding todos and a list of existing todos.
The form uses v-model to bind the input value to newTodo and calls addTodo on submit.
The list of todos is rendered using v-for, and each todo has a delete button that calls deleteTodo.
Script Section:

ref is imported from Vue to create reactive variables.
todos is a reactive array initialized with a default todo.
newTodo is a reactive string for the input value.
addTodo adds the new todo to the list if the input is not empty.
deleteTodo removes a todo from the list by its index.
The reactive variables and functions are returned from the setup function to be used in the template

## Usage

To run the project locally, use the following command:

```
npm run serve

```

or

```
yarn serve
```

This will start the development server, and you can view the app in your browser at http://localhost:8080.

## Contributing

We welcome contributions from everyone. To contribute:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Make your changes and commit them with a descriptive message.
4. Push your changes to your fork.
5. Open a pull request to the main repository.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
