<template>
	<div>
		<h1>To do list in vue.js</h1>
		<div>
			<p>Add new task: {{ newItem }}</p>
			<input type="text" placeholder="task" v-model="newItem" />
			<button @click="addItem">Add</button>
		</div>
		<table class="center">
			<tr>
				<th class="id">ID</th>
				<th>Task</th>
				<th class="state">Status</th>
			</tr>
			<tr
				class="item"
				v-bind:class="{ complited: item.state }"
				v-for="item in items"
				v-bind:key="item.id"
			>
				<td>{{ item.id }}</td>
				<td>{{ item.title }}</td>
				<td class="state">
					<button @click="changeState(item.id)" v-if="!item.state">DONE</button>
				</td>
			</tr>
		</table>
	</div>
</template>

<script>
export default {
	data() {
		return {
			newItem: "Go on a trip to space",
			items: [
				{
					id: 1,
					title:
						"Take a scenic hike in a local national park or nature reserve.",
					state: false,
				},
				{
					id: 2,
					title:
						"Visit a museum or art gallery to appreciate the cultural and historical artifacts.",
					state: false,
				},
				{
					id: 3,
					title: "Try a new recipe and cook a delicious meal from scratch.",
					state: true,
				},
				{
					id: 4,
					title:
						"Go stargazing on a clear night and try to spot constellations.",
					state: true,
				},
				{
					id: 5,
					title:
						"Take a yoga or meditation class to relax and rejuvenate your mind and body.",
					state: false,
				},
				{
					id: 6,
					title:
						"Explore a new neighborhood in your city and discover hidden gems.",
					state: true,
				},
				{
					id: 7,
					title:
						"Attend a live music concert or performance to enjoy some great entertainment.",
					state: true,
				},
				{
					id: 8,
					title:
						"Volunteer for a local charity or community organization and make a positive impact.",
					state: false,
				},
				{
					id: 9,
					title:
						"Have a picnic in a nearby park or beach and enjoy the outdoors.",
					state: false,
				},
				{
					id: 10,
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
.complited td:nth-child(2) {
	opacity: 0.5;
	text-decoration: line-through;
}
.complited td:nth-child(3) {
	background-color: rgb(0, 255, 21);
}
td:nth-child(3) {
	background-color: rgb(255, 0, 0);
}
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
div {
	text-align: center;
}
.center {
	margin-top: 20px;
	margin-left: auto;
	margin-right: auto;
}
.id {
	width: 5%;
}
.state {
	width: 10%;
}
button {
	background-color: rgb(0, 0, 255);
	color: green;
}
</style>
