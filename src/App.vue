<template>
  <main>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
    <header>
      <h1>Car Store</h1>
    </header>

    <div class="new-task-form">
      <TaskForm/>
    </div>

    <nav class="filter">
      <button @click="filter = 'all'">Semua</button>
      <button @click="filter = 'favs'">Pilihan</button>
    </nav>
    
    <div class="task-list" v-if="filter === 'all'">
      <p>Kamu mempunyai {{ taskStore.tasks.length }} pilihan mobil </p>
      <div v-for="task in taskStore.tasks" :key="task.id">
        <TaskDetails :task="task"/>
      </div>
    </div>
    <div class="task-list" v-if="filter === 'favs'">
      <p>Kamu mempunyai {{ taskStore.favs.length }} belanja mobil</p>
      <div v-for="task in taskStore.favs" :key="task.id">
        <TaskDetails :task="task"/>
      </div>
    </div>
  </main>
</template>


<script>
import { ref } from 'vue';
import TaskDetails from './components/TaskDetails.vue';
import TaskForm from './components/TaskForm.vue';
import { useTaskStore } from './stores/TaskStore';

export default {
  components: { TaskDetails, TaskForm },
  setup() {
    const taskStore = useTaskStore();
    const filter = ref('all');

    return { taskStore, filter };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
nav {
  padding: 30px;
}
nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  margin-right: 10px;
}
nav a.router-link-exact-active {
  color: #42b983;
}
header {
  background-color: #f8f8f8;
  padding: 20px;
  margin-bottom: 30px;
}
h1 {
  font-family: Copperplate;
  font-size: 36px;
  font-weight: bold;
  margin: 0;
}
.filter {
  padding: 10px;
  background-color: #f8f8f8;
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
}
.filter button {
  padding: 8px 16px;
  margin-right: 10px;
  background-color: #2196F3;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
.filter button:hover {
  background-color: #42b983;
}
.task-list {
  font-family: Monospace;
  margin-top: 20px;
}
.task-list p {
  font-weight: bold;
  font-size: 18px;
  margin-bottom: 10px;
}
.task-list div {
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 10px;
  background-color: #f9f9f9;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}
.task-list div:hover {
  background-color: #e0e0e0;
}
.main-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}
.new-task-form {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}
.task-buttons button {
  padding: 10px;
  margin-left: 10px;
  font-size: 16px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.task-buttons button:hover {
  background-color: #42b983;
}
.todo-list {
  list-style: none;
  padding: 0;
}
.todo-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  padding: 10px;
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  border-radius: 5px;
}
.completed {
  text-decoration: line-through;
}
.todo-buttons button {
  padding: 5px 10px;
  margin-right: 5px;
  font-size: 14px;
  background-color: #000000;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
#copyright {
  text-align: center;
  width: 100%;
  padding: 50px 0;
  margin-top: 50px;
}
.header-container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}
h1 {
  margin: 0;
}
</style>