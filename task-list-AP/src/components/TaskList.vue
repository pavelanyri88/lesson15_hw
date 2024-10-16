<!-- src/components/TaskList.vue -->
<template>
    <div>
      <h1>Список задач</h1>
      
      <p>Общее количество задач: {{ totalTasks }}</p>
      <p>Выполненных задач: {{ completedTasks }}</p>
      
      <TaskForm @add-task="addTask" />
      
      <ul>
        <li v-for="task in tasks" :key="task.id">
          <Task :task="task" @delete-task="deleteTask" />
        </li>
      </ul>
      
    </div>
  </template>
  
  <script>
  import Task from './Task.vue';
  import TaskForm from './TaskForm.vue';
  
  export default {
    name: 'TaskList',
    components: {
      Task,
      TaskForm
    },
    data() {
      return {
        tasks: [
          { id: 1, title: 'Задача 1', description: 'Прочитать документацию', completed: false },
          { id: 2, title: 'Задача 2', description: 'Создать приложение', completed: false }
        ]
      };
    },
    computed: {
      totalTasks() {
        return this.tasks.length;
      },
      completedTasks() {
        return this.tasks.filter(task => task.completed).length;
      }
    },
    methods: {
      addTask(newTask) {
        this.tasks.push({ ...newTask, id: this.tasks.length + 1 });
      },
      deleteTask(id) {
        this.tasks = this.tasks.filter(task => task.id !== id);
      }
    }
  };
  </script>
  
  <style scoped>
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    padding: 10px;
    background-color: #f0f0f0;
    margin: 5px 0;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  </style>
  