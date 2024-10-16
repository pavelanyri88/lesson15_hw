<template>
  <header>
      <div class="wrapper">
      <h2>Список задач</h2>
      <p>Всего задач: {{ totalTasks }}</p>
      <p>Выполнено задач: {{ completedTasks }}</p>

      <form @submit.prevent="addTask">
        <input v-model="newTask.title" type="text" placeholder="Заголовок задачи" required />
        <textarea v-model="newTask.description" placeholder="Описание задачи" required></textarea>
        <button type="submit">Добавить задачу</button>
      </form>
      
      <div>
    <h1>Детальная информация по заявкам</h1>
    <ul>
       <li v-for="task in tasks" :key="task.id">
        <h3>{{ task.title }}</h3>
        <p>{{ task.description }}</p>
        <button @click="deleteTask(task.id)">Удалить</button>
      </li>
    </ul>
  </div>

      <div v-for="task in tasks" :key="task.id">
        <task 
          :task="task" 
          @delete-task="deleteTask"
          @toggle-completed="toggleCompleted"
        />
      </div>
    </div>
  </header>

  <main>
    
  </main>
</template>

<script>
export default {
    data() {
      return {
        tasks: [
          { id: 1, title: 'Задача 1', description: 'Описание задачи 1', completed: false },
          { id: 2, title: 'Задача 2', description: 'Описание задачи 2', completed: false },
        ],
        newTask: {
        title: '',
        description: ''
      }
      };
    },
    computed: {
      totalTasks() {
        return this.tasks.length;
      },
      completedTasks() {
        return this.tasks.filter(task => task.completed).length;
      },
    },
    methods: {
      addTask(newTask) {
        this.tasks.push({id: this.tasks.length + 1, title: this.newTask.title, description: this.newTask.description, completed: false });
      },
      deleteTask(id) {
        this.tasks = this.tasks.filter(task => task.id !== id);
      },
      toggleCompleted(id) {
        const task = this.tasks.find(task => task.id === id);
        task.completed = !task.completed;
      },
      },
  };
</script>

<style scoped>


 form {
  max-width: auto;
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
