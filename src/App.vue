<template>
  <div id="app">
    <h1>Vue.js To-Do App</h1>
    <input
      v-model="newTask"
      @keyup.enter="addTask"
      placeholder="Add a new task"
    />
    <ul>
      <TodoItem
        v-for="(task, index) in tasks"
        :key="index"
        :task="task"
        @remove="removeTask(index)"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';

export default {
  components: { TodoItem },
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push(this.newTask);
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin: 20px;
}

input {
  padding: 10px;
  width: 300px;
  margin-bottom: 10px;
}
</style>
