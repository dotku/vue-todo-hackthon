<template>
  <div class="simple-container">
    <form @submit.prevent="addTodo" aria-label="a todo form">
      <input v-model="newTodo" class="space-both" aria-label="enter a new todo" />
      <button aria-label="add todo">Add</button>
    </form>
    <input type="checkbox" v-model="ifHideCompleted" name="ifHideCompleted" id="ifHideCompleted" />
    <label for="ifHideCompleted" class="space-both">Hide Completed</label>
    <div>
      <ul v-if="todos.length" class="list">
        <li v-for="todo in filteredTodos" :key="todo.id">
          <input type="checkbox" v-model="todo.done" />
          <span :class="todo.done && 'done'" class="space-both">{{
            todo.content
          }}</span>
          <button @click="deleteTodo(todo)">x</button>
        </li>
      </ul>
      <div v-else>No Content</div>
    </div>
    <div>
      <h3>Todo's Todos:</h3>
      <ul>
        <li>sorting the todos by date</li>
        <li>due dates</li>
        <li>tags</li>
        <li>search/pagination</li>
      </ul>
    </div>
  </div>
</template>

<script>
let id = 0;
export default {
  data() {
    return {
      ifHideCompleted: false,
      newTodo: "",
      todos: [
        { id: ++id, content: "todo1", done: false },
        { id: ++id, content: "todo2", done: false },
        { id: ++id, content: "todo3", done: false },
      ],
    };
  },
  methods: {
    deleteTodo(todo) {
      if (confirm("are you sure? Can't be undone")) {
        this.todos = this.todos.filter((todoItem) => todoItem.id !== todo.id);
      }
    },
    addTodo() {
      this.todos.push({ id: ++id, content: this.newTodo, done: false });
      this.newTodo = "";
    },
  },
  computed: {
    filteredTodos() {
      return this.ifHideCompleted
        ? this.todos.filter((todoItem) => !todoItem.done)
        : this.todos;
    },
  },
};
</script>

<style>
ul.list {
  list-style-type: none;
  text-align: left;
}

li {
  text-align: left;
}

.simple-container {
  width: 360px;
  max-width: 90vw;
  margin: 0 auto;
}

.space-both {
  margin: 0 8px;
}

.done {
  text-decoration: line-through;
}
</style>
