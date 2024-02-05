<template>
	<h3 v-if="task.length === 0">Day without tasks :)</h3>
	<div v-else class="containerCardTasks">
		<div class="contentCard" v-for="taskCard in task" :key="taskCard">
			<h2>{{taskCard}}</h2>
		</div>
	</div>

</template>

<script>
import connectComponents from '@/connectComponents';

export default {
	data() {
		return {
			task: []
		}
	},
	created() {
		connectComponents.$on('taskWriteByUser', (task) => {
			this.task.push(task);
		});
	}
	
}

</script>

<style>
	.containerCardTasks {
		margin-top: 60px;
		width: 60%;
		height: auto;
		display: flex;
		flex-wrap: wrap;

	}
	.contentCard {
		margin: 10px;
		border: 2px solid rgb(6, 3, 3);
		border-radius: 5px ;
		width: 30%;
	}

</style>