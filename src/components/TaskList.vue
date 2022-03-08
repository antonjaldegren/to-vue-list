<script setup>
import { ref } from "vue";
import { v4 as uuid } from "uuid";
import Task from "./Task.vue";

const input = ref("");
const tasks = ref([]);

function addTask() {
	tasks.value.push({ id: uuid(), title: input.value, isCompleted: false });
	input.value = "";
}

function removeTask(task) {
	tasks.value = tasks.value.filter((t) => t !== task);
}
</script>

<template>
	<h1>TO-DO LIST</h1>
	<section class="input-box">
		<div class="input-container">
			<input
				type="text"
				v-model="input"
				@keydown.enter="input.length > 0 ? addTask() : null"
			/>
			<button @click="addTask" :disabled="input.length === 0">
				Add task
			</button>
		</div>
	</section>
	<main>
		<Task
			v-for="task in tasks"
			:key="task.id"
			:data="task"
			@remove="removeTask"
		/>
	</main>
</template>

<style scoped>
h1 {
	text-align: center;
}
.input-box {
	box-shadow: 0 3px 5px rgba(57, 63, 72, 0.185);
	border: 1px solid rgb(233, 233, 233);
	background: rgb(250, 250, 250);
	padding: 1em;
	margin: 1em 1em 0;
	box-sizing: border-box;
}

.input-container {
	width: 100%;
	display: flex;
}

.input-container input {
	height: 2.5rem;
	border: 1px solid rgb(218, 218, 218);
	border-right: none;
	border-bottom-left-radius: 5px;
	border-top-left-radius: 5px;
	box-sizing: border-box;
	padding: 1em;
	font-size: 1rem;
	flex-grow: 1;
	flex-shrink: 0;
}

.input-container input:focus {
	outline: none;
	border: 2px solid #24c8b0;
	border-right: none;
}

.input-container button {
	height: 2.5rem;
	border: none;
	border-bottom-right-radius: 5px;
	border-top-right-radius: 5px;
	border-left: none;
	background: #24c8b0;
	color: white;
	padding: 0 1em;
	font-size: 1rem;
	flex-shrink: 0;
}

.input-container button:hover:enabled {
	cursor: pointer;
	background: #00bb9f;
}
</style>
