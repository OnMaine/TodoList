<template>
  <li class="border border-teal-300 text-teal-700 flex justify-between py-2 px-8 my-4">
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox"
             v-on:change="todo.completed = !todo.completed">
      <strong class="ml-3">{{ index + 1 }}</strong>
      {{ todo.title | uppercase }}
    </span>
    <button class="bg-teal-400 text-white px-2"
            v-on:click="$emit('remove-todo', todo.id)"
    >&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>
.done {
  @apply line-through;
}
</style>
