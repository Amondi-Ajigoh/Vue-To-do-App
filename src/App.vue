<template>
  <div id="app">
    <h1>Todo List</h1>
    <input type="text" v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task" />
    <button @click="addTodo">Add</button>

    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input type="checkbox" v-model="todo.completed" />
        <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newTodo: "", // Stores the new task input
      todos: []    // Stores the list of tasks
    };
  },
  methods: {
    addTodo() {
      // Adds a new todo to the list
      if (this.newTodo.trim() !== "") {
        this.todos.push({ text: this.newTodo.trim(), completed: false });
        this.newTodo = ""; // Clear the input field
      }
    },
    removeTodo(index) {
      // Removes a todo from the list
      this.todos.splice(index, 1);
    }
  }
};
</script>
<style scoped>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
}

input[type="text"] {
  margin-bottom: 10px;
  padding: 5px;
  width: 200px;
}

button {
  margin-left: 5px;
  padding: 5px 10px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 10px 0;
}

.completed {
  text-decoration: line-through;
  color: gray;
}
</style>
