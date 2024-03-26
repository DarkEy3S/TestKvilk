<template>
  <div class="task-input my-list">
    <input v-model="title" placeholder="Заголовок" type="text" />
    <input v-model="description" placeholder="Описание" type="text" />
    <button @click="onAddTask">Добавит задачу</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  emits: {
    onAddTask({ title, description }) {
      if (title === '' || description === '') {
        alert('Fill some info please!')
        return false
      }
      return true
    }
  },
  setup(props, { emit }) {
    const title = ref('')
    const description = ref('')

    const onAddTask = () => {
      emit('onAddTask', { title: title.value, description: description.value })
    }

    return {
      title,
      description,
      onAddTask
    }
  }
}
</script>

<style scoped>
.task-input {
  margin: 10px 0;
}
</style>
