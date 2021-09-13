<template>
  <ToDoList
    name="Today's Tasks"
    :tasks="tasks"
    @delete-task="deleteTask"
    @add-task="addTask"
  />
</template>

<script>
import ToDoList from "./components/ToDoList";
export default {
  name: "App",
  components: {
    ToDoList,
  },
  methods: {
    deleteTask(id) {
      if (confirm("Sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
        let i;
        for (i in this.tasks) {
          this.tasks[i].id = parseInt(i) + 1;
        }
      }
    },
    addTask(task) {
      this.tasks.push({
        id: this.tasks.length + 1,
        title: task,
        important: false,
        done: false,
      });
    },
  },
  data() {
    return {
      tasks: [
        { id: 1, title: "Go swimming", important: false, done: false },
        { id: 2, title: "Fix the light", important: false, done: true },
        { id: 3, title: "Buy a new t-shirt", important: false, done: true },
        { id: 4, title: "Workout", important: false, done: false },
        { id: 5, title: "Call Mom", important: true, done: false },
        { id: 6, title: "Launch with Sam", important: true, done: false },
        { id: 7, title: "Spanish Class", important: true, done: true },
        { id: 8, title: "Watch some TED Talks", important: false, done: false },
      ],
    };
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
  margin: 60px auto 20px;
}
</style>
