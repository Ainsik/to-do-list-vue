<template>
	<tr class="item" v-bind:class="{ complited: item.state }">
		<td>{{ item.title }}</td>
		<td class="state">
			<button @click="changeState()" v-if="!item.state">DONE</button>
		</td>
	</tr>
</template>

<script>
export default {
	props: ["item"],
	methods: {
		changeState() {
			this.$emit("done", this.item.id);
		},
	},
};
</script>

<style>
.complited td:nth-child(1) {
	opacity: 0.5;
	text-decoration: line-through;
}

.complited td:nth-child(2) {
	background-color: rgb(0, 255, 21);
}

td:nth-child(2) {
	background-color: rgb(255, 0, 0);
}

button {
	background-color: rgb(0, 0, 255);
	color: rgb(211, 173, 7);
}
</style>
