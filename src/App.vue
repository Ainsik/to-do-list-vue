<template>
	<div>
		<h1>To do list in vue.js</h1>
		<Todo />
	</div>
</template>

<script>
import Todo from "./components/ToDoApp.vue";

export default {
	components: {
		Todo,
	},
};
</script>

<style>
div {
	text-align: center;
}
</style>
