<script setup>
import Task from "./Task.vue";
const { tasks } = defineProps({
	tasks: Array,
});
const emit = defineEmits(["remove"]);
</script>

<template>
	<main>
		<Task
			v-for="task in tasks"
			:key="task.id"
			:task="task"
			:remove="() => emit('remove', task)"
		/>
	</main>
</template>

<style scoped>
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
	flex-shrink: 1;
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
