<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" :showAddTask="showAddTask" title="Task Tracker" />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script lang="ts">
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask =  !this.showAddTask
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  margin-left: 25%;
  margin-right: 25%;
}
.float-right {
  float: right;
}
h1 {
  margin-block-start: 1em;
  margin-block-end: 1em;
}
h3 {
  margin-block-start: 0.5em;
  margin-block-end: 0.5em;
}
h6 {
  margin-block-start: 0.3em;
  margin-block-end: 0.3em;
}
.btn {
    text-transform: uppercase;
    vertical-align: bottom;
    border: 0;
    -webkit-box-shadow: 0 2px 5px 0 rgba(0,0,0,.2),0 2px 10px 0 rgba(0,0,0,.1);
    box-shadow: 0 2px 5px 0 rgba(0,0,0,.2),0 2px 10px 0 rgba(0,0,0,.1);
    font-weight: 500;
    padding: .625rem 1.5rem .5rem;
    font-size: .75rem;
    line-height: 1.5;
}
.btn-primary {
  color: #ffffff;
  background-color: #1266f1;
}
.btn-secondary {
  color: #ffffff;
  background-color: #b23cfd;
}
.btn-success {
  color: #ffffff;
  background-color: #00b74a;
}
.btn-danger {
  color: #ffffff;
  background-color: #f93154;
}
</style>
