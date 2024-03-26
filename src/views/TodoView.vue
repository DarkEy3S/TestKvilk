<template>
  <div>
    <TaskInput @onAddTask="addTask"></TaskInput>
    <ul class="task-list my-list">
      <li v-for="item in taskList" :key="item.id">
        <TaskCard
          @onRemove="removeTask(item.id)"
          @onDone="setDoneTask(item.id)"
          :model="item"
        ></TaskCard>
      </li>
    </ul>
  </div>
</template>

<script>
import TaskInput from '../components/TaskInput.vue'
import TaskCard from '../components/TaskCard.vue'
import { ref, onMounted } from 'vue'

export default {
  name: 'App',
  components: {
    TaskCard,
    TaskInput
  },
  setup() {
    const taskList = ref([])

    const loadTasksFromLocalStorage = () => {
      const savedTasks = localStorage.getItem('tasks')
      if (savedTasks) {
        taskList.value = JSON.parse(savedTasks)
      }
    }

    const saveTasksToLocalStorage = () => {
      localStorage.setItem('tasks', JSON.stringify(taskList.value))
    }

    const addTask = ({ title, description }) => {
      taskList.value.push({
        id: taskList.value.length ? taskList.value[taskList.value.length - 1].id + 1 : 0,
        title,
        description,
        status: false
      })
      saveTasksToLocalStorage()
    }

    const setDoneTask = (id) => {
      taskList.value.forEach((task) => {
        if (task.id === id) {
          task.status = true
        }
      })
      saveTasksToLocalStorage()
    }

    const removeTask = (id) => {
      taskList.value = taskList.value.filter((task) => task.id !== id)
      saveTasksToLocalStorage()
    }

    onMounted(() => {
      loadTasksFromLocalStorage()
    })

    return {
      taskList,
      addTask,
      removeTask,
      setDoneTask
    }
  }
}
</script>

<style scoped>
.task-list {
  list-style: none;
}
</style>
