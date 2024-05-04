<template>
  <div id="app">
    <h1>Todo List</h1>
    <form @submit.prevent="addTask">
      <input v-model="newTask" placeholder="Tambahkan tugas baru" />
      <button type="submit">Tambah</button>
    </form>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <span :class="{ completed: task.completed }">{{ task.text }}</span>
        <button @click="toggleTaskCompletion(index)">
          {{ task.completed ? 'Belum Selesai' : 'Selesai' }}
        </button>
        <button @click="deleteTask(index)">Hapus</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [
        { text: 'Belajar Vue.js', completed: true },
        { text: 'Mengerjakan tugas', completed: true },
        { text: 'Olahraga', completed: false },
      ],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({ text: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    toggleTaskCompletion(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
.completed {
  text-decoration: line-through;
  color: gray;
}
</style>