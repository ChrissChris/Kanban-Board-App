<template>
	<div class="container mt-5">
		<div class="row">
			<div class="col form-inline">
				<b-form-input
					id="input-2"
					v-model="newTask"
					required
					placeholder="Please enter your task"
					@keyup.enter="add"
				></b-form-input>
				<b-button @click="add" variant="primary" class="ml-3">Add</b-button>
			</div>
		</div>
		<div class="row mt-5">
			<div class="col-3">
				<div class="p-2 alert alert-secondary">
					<h3>Back Log</h3>
					<!-- Backlog draggable component. Pass arrBackLog to list prop -->
					<draggable class="list-group kanban-column" :list="arrBackLog" group="tasks">
						<div
							class="list-group-item"
							v-for="element in arrBackLog"
							:key="element.name"
						>{{ element.name }}</div>
					</draggable>
				</div>
			</div>

			<div class="col-3">
				<div class="p-2 alert alert-primary">
					<h3>In Progress</h3>
					<!-- In Progress draggable component. Pass arrInProgress to list prop -->
					<draggable class="list-group kanban-column" :list="arrInProgress" group="tasks">
						<div
							class="list-group-item"
							v-for="element in arrInProgress"
							:key="element.name"
						>{{ element.name }}</div>
					</draggable>
				</div>
			</div>

			<div class="col-3">
				<div class="p-2 alert alert-warning">
					<h3>Half Done</h3>
					<!-- Testing draggable component. Pass arrTested to list prop -->
					<draggable class="list-group kanban-column" :list="arrTested" group="tasks">
						<div
							class="list-group-item"
							v-for="element in arrTested"
							:key="element.name"
						>{{ element.name }}</div>
					</draggable>
				</div>
			</div>

			<div class="col-3">
				<div class="p-2 alert alert-success">
					<h3>Done</h3>
					<!-- Done draggable component. Pass arrDone to list prop -->
					<draggable class="list-group kanban-column" :list="arrDone" group="tasks">
						<div class="list-group-item" v-for="element in arrDone" :key="element.name">{{ element.name }}</div>
					</draggable>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import draggable from "vuedraggable";

export default {
	name: "KanbanBoard",
	components: {
		draggable,
	},
	data() {
		return {
			newTask: " ",
			arrBackLog: [
				{ name: "Morning Coffee / Tea" },
				{ name: "Code Sign Up Page" },
				{ name: "Test Dashboard" },
				{ name: "Style Registration" },
				{ name: "Help with Designs" },
			],
			arrInProgress: [],
			arrTested: [],
			arrDone: [],
		};
	},
	methods: {
		add() {
			if (this.newTask) {
				this.arrBackLog.push({ name: this.newTask });
				this.newTask = " ";
			}
		},
	},
};
</script>

<style lang="css" scoped>
/* Here we set our  action colums to have default height-size  300px */

.kanban-column {
	min-height: 300px;
}
</style>