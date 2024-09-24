<template>
  <div class="todo-app">
    <h1>Todo List</h1>
    
    <div class="todo-input">
      <input v-model="newTodo" placeholder="Add a new todo" @keyup.enter="addTodo" />
      <button :disabled="!newTodo.trim()" @click="addTodo">Add</button>
    </div>

    <ul class="todo-list">
      <li v-for="(todo, index) in todos" :key="index" class="todo-item">
        <span>{{ todo.text }}</span>
        <button @click="removeTodo(index)" class="remove-btn">Remove</button>
      </li>
    </ul>

    <p v-if="todos.length === 0" class="no-todos">No todos yet, add one!</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({ text: this.newTodo });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.todo-app {
  max-width: 500px;
  margin: 50px auto;
  padding: 20px;
  background-color: #f7f7f7;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
  font-family: 'Arial', sans-serif;
}

h1 {
  color: #333;
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.todo-input {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.todo-input input {
  width: 60%;
  padding: 10px;
  font-size: 1.1rem;
  border: 2px solid #ddd;
  border-radius: 5px;
  margin-right: 10px;
  outline: none;
}

.todo-input button {
  padding: 10px 20px;
  font-size: 1rem;
  background-color: #28a745;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.todo-input button:disabled {
  background-color: #ddd;
  cursor: not-allowed;
}

.todo-input button:not(:disabled):hover {
  background-color: #218838;
}

.todo-list {
  list-style-type: none;
  padding: 0;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fff;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.todo-item span {
  font-size: 1.2rem;
}

.remove-btn {
  background-color: #dc3545;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.remove-btn:hover {
  background-color: #c82333;
}

.no-todos {
  font-size: 1.2rem;
  color: #777;
}
</style>
