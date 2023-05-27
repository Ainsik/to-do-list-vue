<template>
	<div>
		<div>
			<p>Add new task: {{ newItem }}</p>
			<input type="text" placeholder="task" v-model="newItem" />
			<button @click="addItem">Add</button>
		</div>
		<table class="center">
			<tr>
				<th>Task</th>
				<th class="state">Status</th>
			</tr>
			<TaskToDo
				:item="item"
				v-for="item in items"
				:key="item.id"
				@done="changeState"
			/>
		</table>
	</div>
</template>

<script>
import TaskToDo from "./TaskToDo.vue";

export default {
	components: {
		TaskToDo,
	},
	data() {
		return {
			newItem: "Go on a trip to space.",
			items: [
				{
					id: 1,
					title:
						"Go stargazing on a clear night and try to spot constellations.",
					state: false,
				},
				{
					id: 2,
					title:
						"Explore a new neighborhood in your city and discover hidden gems.",
					state: false,
				},
				{
					id: 3,
					title:
						"Start a new hobby or learn a new skill, such as painting, playing a musical instrument, or coding.",
					state: true,
				},
			],
		};
	},
	methods: {
		addItem() {
			this.items.push({
				id: this.items.length + 1,
				title: this.newItem,
				state: false,
			});
			this.newItem = "";
		},
		changeState(id) {
			const index = this.items.findIndex((el) => el.id === id);
			var status = this.items[index].state;
			status
				? (this.items[index].state = false)
				: (this.items[index].state = true);
		},
	},
};
</script>

<style>
table {
	font-family: arial, sans-serif;
	border-collapse: collapse;
	width: 50%;
	align-items: center;
}

th {
	font-weight: 600;
}

td,
th {
	border: 1px solid #dddddd;
	text-align: left;
	padding: 8px;
	text-align: center;
}

tr:nth-child(even) {
	background-color: #dddddd;
}

.center {
	margin-top: 20px;
	margin-left: auto;
	margin-right: auto;
}

.state {
	width: 10%;
}
</style>
