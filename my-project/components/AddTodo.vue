<template>
  <form class="mb-5" @submit.prevent="onSubmit">
    <input class="w-56 p-1 bg-teal-300 text-white outline-none" type="text" v-model="title">
    <button class="ml-3 p-1 px-5 bg-teal-300 text-white" type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    }
  },
}
</script>

<style scoped>
</style>
