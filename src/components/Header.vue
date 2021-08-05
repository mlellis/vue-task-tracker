<template>
  <header>
    <h1>
      <div class="float-right">
        <Button v-show="homePage" @btn-click="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add task'" :color="showAddTask ? 'btn-danger' : 'btn-primary'" />
      </div>
      {{ title }}
    </h1>
  </header>
</template>

<script>
  import Button from './Button.vue'

  export default {
    name: 'Header',
    props: {
      title: String,
      showAddTask: Boolean,
    },
    components: {
      Button,
    },
    computed: {
      homePage() {
        if(this.$route.path === '/') {
          return true
        } else {
          return false
        }
      }
    }
  }
</script>

<style scoped>
  header {
    border-bottom: 1px solid #ccc;
  }
</style>
