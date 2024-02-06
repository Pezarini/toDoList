<template>
	<h3 v-if="task.length === 0" id="withoutTasks">Day without tasks :)</h3>
	<div v-else class="containerCardTasks">
		<div 
			class="contentCard" 
			v-for="(taskCard, index) in task" 
			:key="index" >
			<h2>{{ taskCard }}</h2>
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
		};
	},
	created() {
		connectComponents.$on('userWrittenTask', (task) => {
			this.task.push(task);
		});
	},
	methods: {
		removeTask(index) {
			this.task.splice(index, 1);
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
	border: 2px solid rgb(6, 3, 3);
	border-radius: 5px;
	width: 30%;
	}

	.buttonToRemove {
	position: absolute;
	top: 5px;
	right: 5px;
	cursor: pointer;
	}
</style>