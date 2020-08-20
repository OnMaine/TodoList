<template>
  <div id="app" class="container mx-auto">
    <div class="flex flex-col justify-center items-center border-teal-500 border-b-2">
      <h1 class="text-2xl uppercase font-bold mb-4">Todo application</h1>
      <AddTodo
        @add-todo="addTodo"
      />
    </div>
    <div class="">
      <TodoList
        v-bind:todos="todos"
        @remove-todo="removeTodo"
      />
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
      todos: [
        {id: 1, title: 'Купить хлеб', completed: false},
        {id: 2, title: 'Купить пиво', completed: false},
        {id: 3, title: 'Купить жигули', completed: false}
      ]
    };
  },
  components: {
    TodoList,
    AddTodo
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  }
}
</script>

<style>

</style>
