<template>
  <div :style="{ backgroundColor: task.completed ? '#d4edda' : '#f8d7da' }">
    <h3>{{ task.title }}</h3>
    <button @click="deleteTask">Удалить</button>
    <button @click="showDetails = !showDetails">Подробнее</button>
    <input type="checkbox" v-model="task.completed" @change="makeCompleted" /> Выполнено
    
    <slot v-if="showDetails">
      <p>{{ task.description }}</p>
    </slot>
  </div>
</template>

<script>
export default {
  props: ['task'],
  data() {
    return {
      showDetails: false,
    };
  },
  methods: {
    deleteTask() {
      this.$emit('delete-task', this.task.id);
    },
    makeCompleted() {
      this.$emit('toggle-completed', this.task.id);
    },
  },
};
</script>

<style scoped>
h3 {
  margin: 0;
}
button {
  padding: 8px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  margin-right: 6px;
}

button:hover {
  background-color: #0056b3;
}
</style>
