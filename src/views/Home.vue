<template>
  <AddTask @add-task="addTask" v-if="showAddTask" />
  <Tasks @delete-task="deleteTask" @toggle-reminder="toggleReminder" :tasks="tasks" />
</template>

<script>
import Tasks from '../components/Tasks.vue'
import AddTask from '../components/AddTask.vue'

export default {
  name: 'Home',
  props: {
    showAddTask: Boolean,
  },
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    async deleteTask(id) {
      const response = await fetch(`api/tasks/${id}`, {
        method: 'DELETE',
      })

      if (response.status === 200) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      } else {
        alert('Error deleting task')
      }
    },
    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id)
      const updateTask = {...taskToToggle, reminder: !taskToToggle.reminder}

      const response = await fetch(`api/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json'
        },
        body: JSON.stringify(updateTask)
      })

      const data = await response.json()

      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: data.reminder} : task)
    },
    async addTask(task) {
      const response = await fetch('api/tasks', {
        method: 'POST',
        body: JSON.stringify(task),
        headers: {
          'Content-type': 'application/json',
        }
      })

      const data = await response.json()

      this.tasks = [...this.tasks, data]
    },
    async fetchTasks() {
      const result = await fetch('api/tasks')
      const data = await result.json()

      return data
    },
    async fetchTask(id) {
      const result = await fetch(`api/tasks/${id}`)
      const data = await result.json()

      return data
    },
  },
  async created() {
    this.tasks = await this.fetchTasks()
  }
}
</script>
