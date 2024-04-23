<template>
	<div class="containerProgress">
		<h1>Tasks</h1>
		<div class="contentProgress">
			<div 
				class="barProgress"
				:class="{'withoutBorder': this.calculatePercentage === 0}"
				:style="{ width: this.calculatePercentage + '%' }">
			</div>
			<span>{{ this.calculatePercentage + '%' }}</span>
		</div>
	</div>
</template>

<script>
import connectComponents from '@/connectComponents';

export default {
	data() {
		return {
			lengthTask: 0,
			lengthTaskFinished: 0,
		}
	},
	computed: {
		calculatePercentage() {
			if (this.lengthTask === 0) {
				return 0;
			}
			return 100 / this.lengthTask === Infinity ? 0 : Math.floor((this.lengthTaskFinished / this.lengthTask) * 100);
		}
	},
	created() {
		connectComponents.$on('howManyTasks', (lengthTasks) => {
			this.lengthTask = lengthTasks.tasks;
			this.lengthTaskFinished = lengthTasks.tasksFinished;
		});
	},
}
</script>

<style scoped>
	.containerProgress {
		display: flex;
		justify-content: center;
		align-items: center; 
		flex-direction: column;
		width: 100%;
	}

	.contentProgress{
		width: 50%;  
		height: 2rem;
		box-shadow: 7px 7px 10px rgba(0, 0, 0, 0.1);
		display: flex;
	}

	.barProgress {
		display: flex;
		justify-content: center;
		height: 2rem;
		background: rgb(71, 250, 0) ;
	}

	.contentProgress span {
		width: 48%;  
		position: fixed
	}

	.withoutBorder{
		border: none;
	}
</style>