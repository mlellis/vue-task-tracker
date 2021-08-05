<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times float-right"></i>
    </h3>
    <h6>{{ task.day }} </h6>
  </div>
</template>

<script>
  export default {
    name: 'Task',
    props: {
      task: Object
    }
  }
</script>

<style>
  .task {
    text-align: left;
    padding: 10px 25px;
  }
  i {
    color: red;
  }
  .reminder {
    border-left: 4px solid green;
  }
</style>
