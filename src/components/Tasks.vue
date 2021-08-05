<template>
  <div v-for="task in tasks" :key="task.id" class="tasks">
    <Task @delete-task="$emit('delete-task', task.id)" @toggle-reminder="$emit('toggle-reminder', task.id)" :task="task" />
  </div>
</template>

<script>
  import Task from './Task.vue'

  export default {
    name: 'Tasks',
    props: {
      tasks: Array
    },
    components: {
      Task,
    },
    emits: ['delete-task', 'toggle-reminder']
  }
</script>

<style>
  .tasks {
    border: 1px solid #ccc;
    border-top: none;
    border-radius: 5px;
  }
</style>
