<template>
	<h3 v-if="task.length === 0" id="withoutTasks">Day without tasks :)</h3>
	<div v-else class="containerCardTasks">
		<div
			class="contentCard"
			v-for="(taskCard, index) in task"
			:key="index"
			:class="{'taskReady': task[index].conditional}"
		>
			<div 
				class="textContentCard"
				@click="doneTask(index)"
			> 
				<h2>{{ taskCard.text }}</h2>
			</div>
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
		const json = localStorage.getItem('task')
		const taskIsArray = JSON.parse(json);
		this.task = Array.isArray(taskIsArray) ? taskIsArray : [];
	},
	watch: {
		task: {
			deep: true,
			handler() {
				localStorage.setItem('task', JSON.stringify(this.task));
			}
		}
	},
	methods: {
		removeTask(index) {
			if (this.task[index].conditional) {
				this.tasksFinished--;
			}

			this.task.splice(index, 1);

			if (this.task.length === 0) {
				this.tasksFinished = 0;
			}

			connectComponents.$emit('howManyTasks', {tasks: this.task.length, tasksFinished: this.tasksFinished});
		},
		doneTask(index) {
			this.task[index].conditional = !this.task[index].conditional;
	
			if (!this.task[index].conditional) {
				this.tasksFinished--;
			}
			else {
				this.tasksFinished++;	
			}
	
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
		min-width: 60%;
		width: auto;
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