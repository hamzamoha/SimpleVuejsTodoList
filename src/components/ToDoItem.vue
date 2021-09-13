<template>
  <div
    class="todo-item"
    :class="[task.important ? 'important' : '', task.done ? 'done' : '']"
  >
    <span @click="toggleDone">{{ task.title }}</span>
    <button @click="$emit('delete-task', task.id)">X</button>
    <button class="pin" @click="toggleImportant" style="right: 50px">
      <svg
        aria-hidden="true"
        focusable="false"
        data-prefix="fas"
        data-icon="thumbtack"
        role="img"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 384 512"
        class="svg-inline--fa fa-thumbtack fa-w-12"
      >
        <path
          fill="currentColor"
          d="M298.028 214.267L285.793 96H328c13.255 0 24-10.745 24-24V24c0-13.255-10.745-24-24-24H56C42.745 0 32 10.745 32 24v48c0 13.255 10.745 24 24 24h42.207L85.972 214.267C37.465 236.82 0 277.261 0 328c0 13.255 10.745 24 24 24h136v104.007c0 1.242.289 2.467.845 3.578l24 48c2.941 5.882 11.364 5.893 14.311 0l24-48a8.008 8.008 0 0 0 .845-3.578V352h136c13.255 0 24-10.745 24-24-.001-51.183-37.983-91.42-85.973-113.733z"
          class=""
        ></path>
      </svg>
    </button>
  </div>
</template>
<script>
export default {
  name: "ToDoItem",
  props: {
    task: Object,
  },
  methods: {
    toggleDone() {
      this.task.done = !this.task.done;
    },
    toggleImportant() {
      this.task.important = !this.task.important;
    },
  },
};
</script>
<style scoped>
.todo-item {
  text-align: left;
  width: 300px;
  margin: 15px auto;
  position: relative;
}
.todo-item button {
  border: 0;
  position: absolute;
  top: 10px;
  right: 10px;
  line-height: 30px;
  width: 30px;
  border-radius: 50%;
  cursor: pointer;
  transition: all 0.2s;
  height: 30px;
}
.todo-item button:hover {
  background-color: #ff5454;
  color: #eee;
}
span {
  padding: 0 10px;
  line-height: 50px;
  display: block;
  background-color: #fff;
  box-shadow: 0 2px 5px -4px #00000060;
  cursor: pointer;
}
button svg {
  height: 12px;
  margin: 9px 0;
}
.done span {
  text-decoration: line-through;
  color: #a5a5a5;
  box-shadow: none;
}
.important:not(.done) {
  order: -1;
}
.done:not(.important) {
  order: 2;
}
.important.done {
  order: 1;
}
.important .pin {
  background-color: #ff5454;
  color: #eee;
}
.important.done .pin {
  background-color: #f88;
  color: #eee;
}
</style>