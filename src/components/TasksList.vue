<template>
  <div class="todo-items">
    <button @click="inputVisible = !inputVisible; newTask = ''">{{ (inputVisible)? 'Close': '+ new Task' }}</button>
	<div class="input" v-if="inputVisible">
		<input type="text" v-model="newTask">
		<button @click="if(newTask && newTask != '') {$emit('add-task', newTask); newTask = ''}">Add</button>
	</div>
    <ToDoItem
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @delete-task="$emit('delete-task', $event)"
    />
  </div>
</template>
<script>
import ToDoItem from "./ToDoItem";

export default {
  name: "TasksList",
  props: {
    tasks: Array,
  },
  components: {
    ToDoItem,
  },
  data() {
	  return {
		  inputVisible: false
	  }
  }
};
</script>
<style scoped>
.input {
	order: -1;
	width: 300px;
	margin: 15px auto;
	position: relative;
}
.input button {
	position: absolute;
	top: 10px;
	right: 10px;
	line-height: 30px;
	width: 30px;
	border: none;
	border-radius: 50%;
	background-color: #aea;
	color: #555;
	cursor: pointer;
	font-size: 9.8px;
}
.input button:hover {
	background-color: #92ce92;
}
.input input {
	display: block;
	width: 100%;
	line-height: 50px;
    box-shadow: 0 2px 5px -4px #00000060;
	border: 0;
	outline: none;
	text-indent: 10px;
	color: #555;
	font-size: 100%;
}
.todo-items {
  display: flex;
  flex-direction: column;
}
.todo-items > button {
  order: -1;
  width: 300px;
  margin: 15px auto;
  height: 50px;
  border-radius: 0;
  border: 2px dashed;
  color: #888;
  font-size: 20px;
  cursor: pointer;
}
.todo-items > button:hover {
  color: #aaa;
}
</style>
