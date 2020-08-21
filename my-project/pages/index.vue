<template>
  <div id="app" class="container mx-auto">
    <div class="flex flex-col justify-center items-center border-teal-500 border-b-2">
      <h1 class="text-2xl uppercase font-bold mb-4">Todo application</h1>
      <AddTodo
        @add-todo="addTodo"
      />
      <select v-model="filter" class="text-white px-5 py-1 mb-5 bg-teal-300 outline-none font-bold border border-white">
        <option value="all">All</option>
        <option value="completed">Completed</option>
        <option value="not-completed">Not Completed</option>
      </select>
    </div>
    <div>
      <TodoList
        v-if="filteredTodos.length"
        v-bind:todos="filteredTodos"
        @remove-todo="removeTodo"
      />
      <p v-else class="text-teal-400 text-center font-bold text-lg pt-4">No todos!</p>
    </div>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'

export default {
  name: 'app',
  data() {
    return {
      todos: [],
      filter: 'all'
    };
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      }

      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }

      if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      }
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList,
    AddTodo
  }
}
</script>

<style>

</style>
