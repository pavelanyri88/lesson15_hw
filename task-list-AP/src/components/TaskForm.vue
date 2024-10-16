<template>
  <form @submit.prevent="submitForm">
    <input v-model="title" type="text" placeholder="Заголовок задачи" required />
    <textarea v-model="description" placeholder="Описание задачи" required></textarea>
    <button type="submit">Добавить задачу</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      description: '',
    };
  },
  methods: {
    submitForm() {
      const newTask = {
        title: this.title,
        description: this.description,
      };
      this.$emit('add-task', newTask);
      this.title = '';
      this.description = '';
    },
  },
};
</script>

<style scoped>
form {
  width: 600px;
  margin-bottom: 10px;
  margin-top: 10px;
}
  input, textarea {
  padding: 8px;
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 8px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
}

button:hover {
  background-color: #0056b3;
}
</style>