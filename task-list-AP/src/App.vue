<!-- src/App.vue -->
<template>
  <div id="main">
    <TaskList />
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue';

export default {
  name: 'taskList',
  components: {
    TaskList
  }
};
</script>

<style>
#main {
width: 600px;
}
</style>
