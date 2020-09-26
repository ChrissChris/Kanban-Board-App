
<template >
	<div id="app">
		<kanban-board></kanban-board>
	</div>
</template>

<script>
import KanbanBoard from "./components/KanbanBoard";

export default {
	name: "App",
	components: {
		KanbanBoard,
	},
};
</script>

<style lang="css">
</style>
