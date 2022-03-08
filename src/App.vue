<script setup>
import { ref } from "vue";
import { v4 as uuid } from "uuid";
import TaskList from "./components/TaskList.vue";
import InputBox from "./components/InputBox.vue";

const tasks = ref([]);

function addTask(input) {
	tasks.value.push({ id: uuid(), title: input, isCompleted: false });
}

function removeTask(task) {
	tasks.value = tasks.value.filter((t) => t !== task);
}
</script>

<template>
	<h1>TO-DO LIST</h1>
	<InputBox @add="addTask" />
	<TaskList :tasks="tasks" @remove="removeTask" />
</template>

<style>
* {
	box-sizing: border-box;
}

h1 {
	text-align: center;
}

#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	max-width: 600px;
	margin: 0 auto;
}
</style>
