<template>
  <form class="mb-5" @submit.prevent="onSubmit">
    <input class="w-56 p-1 bg-teal-300 text-white outline-none border-2 border-white " type="text" v-model="title">
    <button class="btn-submit" type="submit">Create</button>
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

<style>
.btn-submit {
  @apply ml-3 p-1 px-5 border-2 border-white bg-teal-300 text-white font-bold;
  &:hover {
    @apply bg-white border-2 border-teal-300 text-teal-300;
  }
}
</style>
