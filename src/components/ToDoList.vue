<template>
    <div class="todo-list">
        <h3>{{name}}</h3>
        <TasksList :tasks='tasks' @delete-task='$emit("delete-task", $event)' @add-task='$emit("add-task", $event)'/>
    </div>
</template>
<script>
import TasksList from './TasksList';

export default {
    name: 'ToDoList',
    props: {
        name: String,
        tasks: Array
    },
    components: {
        TasksList
    },
}
</script>
<style scoped>

</style>