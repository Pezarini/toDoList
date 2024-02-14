<template>
	<h3 v-if="task.length === 0" id="withoutTasks">Day without tasks :)</h3>
	<div v-else class="containerCardTasks">
		<div
			class="contentCard"
			v-for="(taskCard, index) in task"
			:key="index"
			:class="{'taskReady': task[index].conditional}"
			@click="doneTask(index)">
			<h2>{{ taskCard.text }}</h2>
			<button class="buttonToRemove" @click="removeTask(index)">X</button>
		</div>
	</div>

</template>

<script>
	import connectComponents from '@/connectComponents';

export default {
	data() {
		return {
			task: [],
			tasksFinished: 0,
		};
	},
	created() {
		connectComponents.$on('taskInput', (task) => {
			this.task.push({text: task, conditional: false});
		});
	},
	methods: {
		removeTask(index) {
			this.task.splice(index, 1);
			this.task[index].conditional = false;
			connectComponents.$emit('howManyTasks', this.task.length);
		},
		doneTask(index) {
			this.task[index].conditional = !this.task[index].conditional;
	
			if (!this.task[index].conditional) {
				this.tasksFinished -= 2;
			}
			this.tasksFinished += 1;
			connectComponents.$emit('howManyTasks', {tasks: this.task.length, tasksFinished: this.tasksFinished});
		},
	}
};
</script>

<style>
	#withoutTasks {
		margin-top: 60px;
	}

	.containerCardTasks {
		margin-top: 60px;
		width: 60%;
		height: auto;
		display: flex;
		flex-wrap: wrap;
	}

	.contentCard {
		position: relative;
		margin: 10px;
		border-radius: 5px;
		background: #dedede;
		box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.1); 
		width: 30%;
	}

	.buttonToRemove {
		position: absolute;
		top: 5px;
		right: 5px;
		cursor: pointer;
	}

	.taskReady {
		background-color: rgb(27, 235, 27);
	}
</style>