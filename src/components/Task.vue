<script setup>
const props = defineProps({
	task: Object,
	remove: Function,
});
const emit = defineEmits(["remove"]);
</script>

<template>
	<section>
		<div class="title-container">
			<input type="checkbox" v-model="task.isCompleted" />
			<h2 :class="{ completed: task.isCompleted }">
				{{ task.title }}
			</h2>
		</div>
		<div class="remove-button" @click="remove"></div>
	</section>
</template>

<style scoped>
section {
	display: flex;
	justify-content: space-between;
	align-items: center;
	box-shadow: 0 3px 5px rgba(57, 63, 72, 0.185);
	border: 1px solid rgb(233, 233, 233);
	margin: 1em 1em 0;
	background: rgb(250, 250, 250);
	padding: 1em;
}

.title-container {
	display: flex;
	align-items: center;
	gap: 1em;
	max-width: 90%;
}

input[type="checkbox"] {
	display: grid;
	place-content: center;
	-webkit-appearance: none;
	appearance: none;
	background-color: white;
	margin: 0;
	font: inherit;
	width: 2rem;
	height: 2rem;
	border: 1px solid grey;
	border-radius: 5px;
	flex-shrink: 0;
}

input[type="checkbox"]::before {
	content: "";
	width: 1.3rem;
	height: 1.3rem;
	transform: scale(0);
	background-color: grey;
	transition: 200ms transform ease-in-out;
	clip-path: polygon(14% 44%, 0 65%, 50% 100%, 100% 16%, 80% 0%, 43% 62%);
}

input[type="checkbox"]:checked::before {
	transform: scale(1);
}

h2 {
	font-size: 1.6rem;
	margin: 0;
	text-transform: uppercase;
	overflow: hidden;
	text-decoration: line-through;
	text-decoration-color: transparent;
	transition: 200ms all ease-in-out;
}

.remove-button {
	display: flex;
	justify-content: center;
	align-items: center;
	background: rgb(246, 112, 112) url("../assets/x.svg");
	background-size: 35%;
	background-repeat: no-repeat;
	background-position: center;
	border: none;
	border-radius: 50%;
	width: 1.8rem;
	height: 1.8rem;
	line-height: 0;
	flex-shrink: 0;
}

.remove-button:hover {
	background-color: rgb(246, 69, 69);
}

.completed {
	text-decoration-color: grey;
	color: grey;
	transition: 200ms all ease-in-out;
}
</style>
